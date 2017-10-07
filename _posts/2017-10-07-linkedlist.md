---
layout: post
title: "linkedlist 구현"
date: 2017-10-07 11:33:27
image: 'http://res.cloudinary.com/dk8luxah1/image/upload/c_scale,w_760,h_400/v1502208952/coding.jpg'
description: LinkedList을 구현해봅시다.
category: 'JAVA'
tags:
- java
- linkedlist
twitter_text: LinkedList을 구현해봅시다.
introduction: LinkedList을 구현해봅시다.
---

LinkedList에서 가장 중요한 것이 바로 노드의 구현입니다. 노드는 실제로 데이터가 저장되는 그릇과 같은 것이고 객체 Node는 내부적으로 data와 next 변수를 가지고 있습니다.

코딩을 통해 더 자세히 봐봅시다!


```java

public class Main{
	public static void main(String[] args){

	MyLinkedList list = new MyLinkedList();

        list.add(100);
        list.add(200);
        list.add(400);
        list.add(500);
        System.out.println(list);
		//[100, 200, 400, 500]

        list.add(2, 300);
        list.addFirst(50);
        System.out.println(list);
		//[50, 100, 200, 300, 400, 500]

        System.out.println(list.get(4));
		//400

        list.remove(2);
        list.remove(new Integer(400));
        System.out.println(list);
		//[50, 100, 300, 500]

        list.removeFirst();
        list.removeLast();
        System.out.println(list);
		//[100, 300]

        System.out.println("크기 " + list.size());
		//크기 2

        list.reverseList();
        System.out.println(list);
        //[300, 100]
    }

}


class MyLinkedList {

    private Node header;
    private int size;

	//생성자로 헤더와 사이즈를 초기화해줍니다.
    public MyLinkedList(){

        header = new Node(null);
        size = 0;
    }

    // 단순 연결 리스트 노드
    //data는 노드의 값이고, nextNode는 다음 노드를 가리키는 참조값입니다.
    private class Node{

        private Object data;
        private Node nextNode;

        Node(Object data){

            this.data = data;
            this.nextNode = null;
        }

    }

    // data를 리스트의 첫번째에 삽입합니다.
    public void addFirst(Object data){
        //새로운 노드를 만들어줍니다.
        Node newNode = new Node(data);
        //header에 nextNode가 가리키는 것을 새로운 노드가 가르키게 합니다.
        newNode.nextNode = header.nextNode;
        //새 노드를 header의 nextNode에서 가르키게 합니다.
        header.nextNode = newNode;
        size++;

    }

    // index 위치에 data를 삽입합니다.
    public void add(int index, Object data){

        if(index==0){
            addFirst(data);
            return;
        }
        //추가할 위치의 전, 후 노드를 가져옵니다.
        Node previous = getNode(index-1);
        Node next = previous.nextNode;

        //새로운 노드를 만들고 전, 후 노드와 연결을 해줍니다.
        Node newNode = new Node(data);
        previous.nextNode = newNode;
        newNode.nextNode = next;
        size++;
    }

    // 리스트의 마지막에 data 를 삽입한다.
    public void addLast(Object data){
        add(size, data);
    }

    // 일반적으로 쓰는 add 입니다.
    public void add(Object data){
        addLast(data);
    }

 	// 첫번째 노드를 제거하고 데이터를 반환합니다.
    public Object removeFirst(){
    	//첫번째 노드를 가져와 다음 노드를 가르키는 것을 header의 nextNode에게 가르키게 하고 사이즈를 줄입니다.
        Node firstNode = getNode(0);
        header.nextNode = firstNode.nextNode;
        size--;
        return firstNode.data;

    }

    // index 위치의 노드를 제거하고 데이터를 반환합니다.
    public Object remove(int index){

        if(index<0 || index>=size){

            throw new IndexOutOfBoundsException("Index : " + index + ", Size : " +size);

        }else if(index ==0){

            return removeFirst();

        }
		//제거할 노드를 빼고 연결을 시킵니다.
        Node previous = getNode(index-1);
        Node removeNode = previous.nextNode;
        Node next = removeNode.nextNode;
        previous.nextNode = next;
        size--;

        return removeNode.data;
    }

    // 리스트에서 data를 가진 노드를 제거합니다.
    public boolean remove(Object data){

        int nodeIndex = getNodeIndex(data);

        if(nodeIndex == -1){
            return false;
        }else{
            remove(nodeIndex);
            return true;
        }
    }

    // 리스트의 마지막 노드를 제거하고 데이터를 반환합니다.
    public Object removeLast(){
        return remove(size-1);
    }

	// index 위치의 노드 데이터를 반환합니다.
    public Object get(int index){
        return getNode(index).data;
    }

    // index 위치의 노드를 반환합니다.
    private Node getNode(int index){

        if(index < 0 || index >= size){
            throw new IndexOutOfBoundsException("Index : " + index + ", Size : " + size);
        }
		//우선 헤더 다음노드를 저장하고 index수만큼 노드를 업데이트해줍니다.
        Node node = header.nextNode;
        for(int i =0; i < index; i++){
            node = node.nextNode;
        }

        return node;
    }

    // 첫번째 노드의 데이터를 반환합니다.
    public Object getFirst(){
        return get(0);
    }

    // 해당 데이터의 노드 위치 index를 반환합니다.
    public int getNodeIndex(Object obj){

        if(size<=0){
            return -1;
        }

        int index=0;
        Node node = header.nextNode;
        Object nodeData = node.data;

        // header에서 부터 순차적으로 nodeData와 값을 비교합니다.
        while(!obj.equals(nodeData)){
            node = node.nextNode;

            if(node==null){
                return -1;
            }

            nodeData = node.data;
            index++;
        }

        return index;
    }

    //리스트를 거꾸로 바꾸는 함수입니다.
    public void reverseList(){
    	//header의 nextNode를 next노드에다가 넣습니다.
    	Node next = header.nextNode;
    	Node current = null;
    	Node prev = null;
    	//next노드가 존재한다면 다 한칸씩 nextNode로 넘어가고 current의 nextNode가 이전 노드를 가르키게 합니다.
    	while(next!=null){
    		prev = current;
    		current = next;
    		next = next.nextNode;
    		current.nextNode = prev;
    	}
    	//더 이상의 노드가 없을 때 current를 header의 nextNode가 가르키게 합니다.
    	header.nextNode = current;
    }

    // 리스트의 크기를 반환합니다.
    public int size(){
        return size;
    }

    // 리스트의 데이터 String으로 반환
    public String toString(){

        StringBuffer result = new StringBuffer("[");
        Node node = header.nextNode;

        if(node!=null){
            result.append(node.data);
            node = node.nextNode;

            while(node != null){
                result.append(", ");
                result.append(node.data);
                node = node.nextNode;
            }
        }

        result.append("]");
        return result.toString();
    }

}

```



























