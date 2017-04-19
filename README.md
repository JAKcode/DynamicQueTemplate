#ifndef DYNAMICQUETEMPLATE_H
#define DYNAMICQUETEMPLATE_H
//DynamicTemplateQueue
#include <iostream>
#include <string>
#include <cstdlib>
using namespace std;
template <class T>
class Queue
{
private:
	struct NodeStruct
	{
		T val; //Stores Values
		NodeStruct * next; //Progresses the node the the next node of the list
	};
	NodeStruct * Rear; // Requires a pointer to the end of the list (This is useful for inserting data at the end of the list)
	NodeStruct * Front; // Requires a pointer to the front of the list (This is useful for removing data from the list)
	Queue() //Constructor
{
	Rear = NULL; //List begins with the end equal to empty
	Front = NULL; //List begins with the front equal to empty
}
	~Queue(); //Destructor
void Enqueue (T); //Adds values to the list
void Dequeue ();//Removes values from the list
void Display ();//Displays the list
};
template <class T>
Queue<T>::~Queue()
{	Node Struct * NodePtr, *NodeNext;
	while (NodePtr != NULL) //If the list is not empty
		NodeNext = NodePtr->next; // Traversal pointer is set to point to the next node
	delete NodePtr; //Node is deleted
	NodePtr = NodeNext; //NodePtr is now pointing to the traversal pointer
}
template <class T>
void Queue<T>::Enqueue(T num)
{
	//Variable that holds input data  !!!!!MUST CHANGE THIS TO BE READ IN FOR TEMPLATE TO FUNCTION!!!!! ***CORRECTED?***
	node * temp = new node; // Dynamic Traversal Pointer
	//Input from user **CHANGED TO PARAMETER**
	temp -> val = num; //Private variable within node is set to user input ****Recently changed to Template data type****
	temp -> NULL;//traversal pointer no longer contains data
	if (Front == NULL) //If the list is empty when the value is added
	{
		Front = temp; //Front is now pointing to the node that temp is (If list is empty first node should be the Front)
	}
	else
	{
		Rear ->next = temp; //The traversal pointer is set to the node after rear, for future entry (If list is not empty, Rear is not the same node as Front)
	}
	Rear = temp;//Set the Rear node pointing to the node temp is now pointing to (Either front[if first node], or the next node after the last node Rear was pointing to)

} 
template <class T>
void Queue<T>:: Dequeue()
{
	Node Struct * NodePtr, * NodeTemp;
	while (Front!=NULL)
	{
		NodePtr	= Front; // Pointer to the beginning node
		NodeTemp = NodePtr->next;  //NodeTemp Points to node after Front 
		delete NodePtr; //First Node in the list is deleted
		NodePtr = NodeTemp; //Pointer is set to the new first node
		Front = NodePtr; // Front is redeclared as the new first node
	}
}
template <class T>
void Queue<T>::Display()
{
	Node Struct * showval
	if (Front!=NULL)
	{
	while (Front!=NULL)
	{
		showval = Front; //Pointer showval is now pointing the the Front node
		cout << showval->val; // Need to insert  outside variable to be equal to the data stored in the Front node **Just Displaying Value**
		showval->next; //Progress the pointer to the node after the one that was just displayed
		Front = showval; //Front node should now be pointing to the node after the recently displayed one
	}
	}
	else
	{
		cout << "List is empty";
	}
}
