# LinkedHashMap @author:sudhir
Custom Implementation of LinkedHashMap in java

package com.list;


public class Node {

	public int data;
	@Override
	public String toString() {
		return "Node [data=" + data + ", next=" + next + "]";
	}


	public Node next;
	
	
	public void display() {
		System.out.println(data);
	}
	
}

package com.list;


public class ImplementOwnList {

	public static Node head;

	public boolean isEmpty() {
		return (head == null);

	}
	
	public void addFirst(int data) {
		Node newNode = new Node();
		newNode.data=data;
		newNode.next=head;
		head=newNode;
	}
	public void addLast(int data) {
		
		Node current=head;
		while(current.next!=null) {
			current=current.next;
		}
		Node newNode=new Node();
		newNode.data=data;
		current.next=newNode;
	}
	public Node removeFirst() {
		
		Node temp = head;
		head=head.next;
		return head;
		
	}
	public void removeLast(int node) {
		Node temp = head;
		while(temp.next != null) {
			temp=temp.next;
		}
		if(temp.next!=null) {
			temp.next=temp.next.next;
		}
	}
	public Node insertNthPosition(Node head,int data,int position) {
		
		Node newNode = new Node();
		newNode.next=head;
		Node temp=newNode;
		for(int i=0;i<position;i++) {
			temp=temp.next;
		}
		Node node= new Node();
		node.data=data;
		node.next=temp.next;
		temp.next=node;
		
		return newNode.next;
		
	}
	public Node deleteNthPostion(Node head,int position) {
		Node temp=head;
		if(head==null) {
			return null;
		}
		else if(position==0) {
			return head.next;
		}
		else {
			for(int i=0;i<position;i++) {
				temp=temp.next;
			}
			temp=temp.next.next;
			return head;
		}
		
		
	}
	public int lengthOfLinkedList() {
		Node temp=head;
		int count=0;
		while(temp!=null) {
			temp=temp.next;
			count++;
		}
		
		return count;
		
	}
	public Node nthPostion(Node head,int n) {
		Node firstPointer=head;
		Node secondPointer=head;
		for(int i=0; i<n; i++) {
			firstPointer=firstPointer.next;
		}
		while(firstPointer!=null) {
			firstPointer=firstPointer.next;
			secondPointer=secondPointer.next;
		}
		
		return secondPointer;
		
	}
	Node reverse(Node node) {
		Node next=null;
		Node current=node;
		Node prv=null;
		while(current !=null) {
			next=current.next;
			current.next=prv;
			prv=current;
			current=next;
		}
		node=prv;
		 return node;
		 
	 }
	 void printMiddle() {
		Node firstPostion=head;
		Node secondPostion=head;
		if(firstPostion !=null && firstPostion.next !=null) {
			firstPostion=firstPostion.next.next;
			secondPostion=secondPostion.next;
		}
		  System.out.println("The middle element is [" + 
				  secondPostion.data + "] \n"); 
	 }
	public void printListData() {
		Node current=head;
		while(current!=null) {
			current.display();
			current=current.next;
		}
		
	}
	public static void main(String[] args) {
		ImplementOwnList ownList = new ImplementOwnList();
		ownList.addFirst(12);
		ownList.addFirst(13);
		ownList.addFirst(14);
		
		ownList.printListData();
		System.out.println("--------");
		ownList.addLast(200);
		ownList.printListData();
		System.out.println("----removeFirst----");
		ownList.removeFirst();
		ownList.printListData();
		System.out.println("--------");
		ownList.removeLast(13);
		ownList.printListData();
		System.out.println("----isEmpty----");
		ownList.isEmpty();
		System.out.println(ownList.isEmpty());
		System.out.println("Length of LinkedList:-"+ownList.lengthOfLinkedList());
		ownList.nthPostion(head, 1);
		ownList.printListData();
		System.out.println(ownList.nthPostion(head, 2));
		ownList.insertNthPosition(head, 500, 1);
		ownList.printListData();
		System.out.println("-----postion---");
		ownList.deleteNthPostion(head, 1);
		ownList.printListData();
		ownList.printMiddle();
		ownList.printListData();
	}
}
