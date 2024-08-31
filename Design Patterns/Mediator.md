**Mediator** is a behavioral design pattern that lets you reduce chaotic dependencies between objects. The pattern restricts direct communications between the objects and forces them to collaborate only via a mediator object.


Online Chat System:

this pattern made of two main parts:
1. Mediator class: the central component responsible for connecting objects to each other.
2. User class: objects that need to communicate with each other.

first we need an abstract class or interface to define Mediator.

```python
# Mediator.py

from abc import ABC, abstractmethod


class ChatMediator(ABC):

    @abstractmethod
    def sendMessage(self, message: str, user: "User"):
        pass

    @abstractmethod
    def addUser(self, user: "User"):
        pass

# chatRoom.py

class ChatRoom(ChatMediator):

    def __init__(self):
        self._users = []

    def addUser(self, user: "User"):
        self._users.append(user)

    def sendMessage(self, message: str, user: "User"):
        for u in self._users:
            if u != user:
                u.receiveMessage(message)


# User.py

class User:

    def __init__(self, name: str, chatMediator: ChatMediator):
        self._name = name
        self._chatMediator = chatMediator

    def sendMessage(self, message: str):
        print(f"{self._name} is sending message: {message}")
        self._chatMediator.sendMessage(message, self)

    def receiveMessage(self, message: str):
        print(f"{self._name} received message: {message}")

# main.py

def main():
    chatroom = ChatRoom()

    john = User("John", chatroom)
    alice = User("Alice", chatroom)
    bob = User("Bob", chatroom)

    chatroom.addUser(john)
    chatroom.addUser(alice)
    chatroom.addUser(bob)

    john.sendMessage("Hi Alice!")
    alice.sendMessage("Hey John!")
    bob.sendMessage("Hello everyone!")


if __name__ == "__main__":
    main()

```