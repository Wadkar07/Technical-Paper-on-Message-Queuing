# Messaging Queue

## Introduction to message queuing
Hello reader, thank you for visiting my repository and investing your time, hope it provide you some knowledge about the ```messaging queue```.

Applications designed and written using this interface are known as message queuing applications, because they use the messaging and queuing style:
```
    1. Messaging means that programs communicate by sending each other data in messages rather than calling each other
       directly.
    2. Queuing means that messages are placed on queues in storage, allowing programs to run independently of each
       other, at different speeds and times, in different locations, and without having a logical connection between 
       them.
```
Message queuing has been used in data processing for many years. It is most commonly used today in electronic mail. Without queuing, sending an electronic message over long distances requires every node on the route to be available for forwarding messages, and the addressees to be logged on and conscious of the fact that you are trying to send them a message. In a queuing system, messages are stored at intermediate nodes until the system is ready to forward them. At their final destination they are stored in an electronic mailbox until the addressee is ready to read them. 

Even so, many complex business transactions are processed today without queuing. In a large network, the system might be maintaining many thousands of connections in a ready-to-use state. If one part of the system suffers a problem, many parts of the system become unusable. 

You can think of message queuing as being electronic mail for programs. In a message queuing environment, each program that makes up part of an application suite performs a well-defined, self-contained function in response to a specific request. To communicate with another program, a program must put a message on a predefined queue. The other program retrieves the message from the queue, and processes the requests and information contained in the message. So message queuing is a style of program-to-program communication. 

Queuing is the mechanism by which messages are held until an application is ready to process them. Queuing allows you to:

```
   1. Communicate between programs (which might each be running in different environments) without having to write the
      communication code.
   2. Select the order in which a program processes messages.
   3. Balance loads on a system by arranging for more than one program to service a queue when the number of messages 
      exceeds a threshold.
   4. Increase the availability of your applications by arranging for an alternative system to service the queues if 
      your primary system is unavailable.
```
## What is a message queue?
A message queue, known simply as a queue, is a named destination to which messages can be sent. Messages accumulate on queues until they are retrieved by programs that service those queues.

Queues reside in, and are managed by, a queue manager, (see Message queuing terminology ). The physical nature of a queue depends on the operating system on which the queue manager is running. A queue can either be a volatile buffer area in the memory of a computer, or a data set on a permanent storage device (such as a disk). The physical management of queues is the responsibility of the queue manager and is not made apparent to the participating application programs.

Programs access queues only through the external services of the queue manager. They can open a queue, put messages on it, get messages from it, and close the queue. They can also set, and inquire about, the attributes of queues. 

## Different styles of message queuing

### Point-to-point
```
    1. One message is placed on the queue and one application receives that message.
    2. In point-to-point messaging, a sending application must know information about the receiving application before
       it can send a message to that application. For example, the sending application might need to know the name of 
       the queue to which to send the information, and might also specify a queue manager name.
```
### Publish/Subscribe
```
    1. A copy of each message published by a publishing application is delivered to every interested application.There
       might be many, one, or no interested applications. In publish/subscribe an interested application is known as a
       subscriber and the messages are queued on a queue identified by a subscription.
    2. Publish/subscribe messaging allows you to decouple the provider of information from the consumers of that 
       information. The sending application and receiving application do not need to know as much about each other for
       the information to be sent and received.
```

## Why do we need message queues
### Main features and benefits of message queuing


This information highlights some features and benefits of message queuing. It describes features such as security and data integrity of message queuing.
The main features of applications that use message queuing techniques are:

   #### 1. There are no direct connections between programs.
   ```
   * Message queuing is a technique for indirect program-to-program communication. It can be used within any application where programs communicate with each other. Communication occurs by one program putting messages on a queue (owned by a queue manager) and another program getting the messages from the queue.
    
   * Programs can get messages that were put on a queue by other programs. The other programs can be connected to the same queue manager as the receiving program, or to another queue manager. This other queue manager might be on another system, a different computer system, or even within a different business or enterprise. There are no physical 
connections between programs that communicate using message queues. A program sends messages to a queue owned by a 
queue manager, and another program retrieves messages from the queue.
* As with electronic mail, the individual messages that are part of a transaction travel through a network on a store-and-forward basis. If a link between nodes fails, the message is kept until the link is restored, or the operator or program redirects the message.

The mechanism by which a message moves from queue to queue is hidden from the programs. Therefore the programs are simpler. 
```
   #### 2. Time-independent communication
   ```
   Programs requesting others to do work do not have to wait for the reply to a request. They can do other work, and process the reply either when it arrives or at a later time. When writing a messaging application, you need not know (or be concerned) when a program sends a message, or when the target is able to receive the message. The message is not lost; it is retained by the queue manager until the target is ready to process it. The message stays on the queue until it is removed by a program. This means that the sending and receiving application programs are decoupled; the sender can continue processing without waiting for the receiver to acknowledge receipt of the message. The target application does not even have to be running when the message is sent. It can retrieve the message after it is has been started. 
   ```
#### 3. Small programs
```
   Message queuing allows you to use the advantages of using small, self-contained programs. Instead of a single, large program performing all the parts of a job sequentially, you can spread the job over several smaller, independent programs. The requesting program sends messages to each of the separate programs, asking them to perform their function; when each program is complete, the results are sent back as one or more messages.
   ```
#### 5. Message-driven processing
```
   When messages arrive on a queue, they can automatically start an application using triggering. If necessary, the applications can be stopped when the message (or messages) have been processed. 
```
#### 6. Event-driven processing
```   
   Programs can be controlled according to the state of queues. For example, you can arrange for a program to start as soon as a message arrives on a queue, or you can specify that the program does not start until there are, for example, 10 messages above a certain priority on the queue, or 10 messages of any priority on the queue. 
```   
#### 7. Message priority
```
   * A program can assign a priority to a message when it puts the message on a queue. This determines the position in the queue at which the new message is added.
   * Programs can get messages from a queue either in the order in which the messages are in the queue, or by getting a specific message. (A program might want to get a specific message if it is looking for the reply to a request that it sent earlier.)
```
#### 8. Security
```   
   Security facilities are provided, including authentication of applications when they use a queue manager, authorization checks when they use resources such as a queue on the queue manager, and encryption of message data as it travels over the network, and as it resides on queues. For more information about security, see Security Overview. 
```
#### 9. Data integrity
```
Data integrity is provided by units of work. The synchronization of the start and end of units of work is fully supported as an option on each MQGET or MQPUT, allowing the results of the unit of work to be committed or rolled back. Sync point support operates either internally or externally to IBM® MQ depending on the form of sync point coordination selected for the application. 
```
#### 10.Recovery support
```
For recovery to be possible, all persistent IBM MQ updates are logged. If recovery is necessary, all persistent messages are restored, all in-flight transactions are rolled back, and any sync point commit and backouts are handled in the normal way of the sync point manager in control. For more information about persistent messages, see Message persistence. 
```
