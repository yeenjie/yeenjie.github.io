---
title: 简单排序二叉树(Java实现)
date: 2018-03-08 17:56:09
tags:
---
## 代码实现 ##
```java
package test;
 
import java.util.Arrays;
 
class BinaryTree{//实现二叉树
	private class Node{
		private Comparable data ; //保存的操作数据，因为必须是Comparable子类，而且需要判断大小
		private Node left;
		private Node right;
		@SuppressWarnings("unused")
		public Node(Comparable data) {
			this.data = data;
		}
		public void addNode(Node newNode) {
			if(this.data.compareTo(newNode.data)>0){
				if(this.left == null) {
					this.left = newNode;
				}else {
					this.left.addNode(newNode);
				}
			}else {
				if (this.right == null) {
					this.right=newNode;
				}
				else {
					this.right.addNode(newNode);
				}
			}
		}
		public void toArrayNode() {
			if(this.left!=null){
				this.left.toArrayNode();
			}
			BinaryTree.this.retData[BinaryTree.this.foot++]=this.data;
			if(this.right!=null) {
				this.right.toArrayNode();
			}
		}
	}
	//--------------------------------------//
	private Node root;//任何数据结构一定要抓住根
	private int count;//保存个数
	int foot = 0;
	private Object [] retData;
	public Object [] toArrays(){
		this.foot=0;
		this.retData = new Object[this.count];
		this.root.toArrayNode();
		return this.retData;
	}
	public void add(Object data) {
		//可以保存任何数据
		if(data == null) {
			return ;
		}
		Node newNode = new Node((Comparable) data);
		if(this.root == null) {
			this.root=newNode;
		}else {
			this.root.addNode(newNode);
		}
		this.count++;
	}
}
public class BTDemo {
	public static void main(String[] args) {
		BinaryTree bt = new BinaryTree();
		bt.add("B");
		bt.add("X");
		bt.add("F");
		bt.add("A");
		System.out.println(Arrays.toString(bt.toArrays()));
	}
}

```