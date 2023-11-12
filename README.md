# SE-lab-5
ABBOTTABAD UNIVERSITY OF SCIENCE AND TECHNOLOGY 
Department of Computer Science 
LAB # 5–  






  Class : BSSE-3 C


Subject:  DSA


Submitted By: Muhammad Umair 



Date: 12/11/2023 
Instructor: Jamal Abdul Ahad 


Question 1 :
Implement a basic queue using an array  in python include inqueue Dequeue checking if the queue is empty and finding the size of the queue
class Queue:
    def __init__(self):
        self.items = []

    def is_empty(self):
        return len(self.items) == 0

    def enqueue(self, item):
        self.items.append(item)

    def dequeue(self):
        if not self.is_empty():
            return self.items.pop(0)
        else:
            return "Queue is empty"

    def size(self):
        return len(self.items)
# Create a new queue
my_queue = Queue()

# Enqueue elements
my_queue.enqueue(1)
my_queue.enqueue(2)
my_queue.enqueue(3)

# Check if the queue is empty
print("Is the queue empty?", my_queue.is_empty())

# Dequeue an element
print("Dequeued:", my_queue.dequeue())

# Find the size of the queue
print("Size of the queue:", my_queue.size())

OUTPUT :
Is the queue empty? False
Dequeued: 1
Size of the queue: 


Question 2
Implement a circular queue in python include method of inqueue Dequeue checking if the queue is empty checking if the queue is full and finding the size of the queue

class CircularQueue:
    def __init__(self, capacity):
        self.capacity = capacity
        self.queue = [None] * capacity
        self.front = self.rear = -1

    def isEmpty(self):
        return self.front == -1

    def isFull(self):
        return (self.rear + 1) % self.capacity == self.front

    def inQueue(self, item):
        if self.isFull():
            return "Queue is full"
        elif self.isEmpty():
            self.front = self.rear = 0
        else:
            self.rear = (self.rear + 1) % self.capacity
        self.queue[self.rear] = item

    def dequeue(self):
        if self.isEmpty():
            return "Queue is empty"
        elif self.front == self.rear:
            temp = self.queue[self.front]
            self.front = self.rear = -1
            return temp
        else:
            temp = self.queue[self.front]
            self.front = (self.front + 1) % self.capacity
            return temp

    def size(self):
        if self.isEmpty():
            return 0
        elif self.front <= self.rear:
            return self.rear - self.front + 1
        else:
            return self.capacity - (self.front - self.rear) + 1
OUTPUT :
Is the queue full? False
Dequeued: 1
Size of the queue: 2
