# LpuLive

Interact LpuLive programmatically using a simple Python Library.
Allows you to search, conversation lookup, messages lookup, profile view etc.

## Contents

- [Getting Started](#getting-started)
- [ Methods/Functions ](#Methods)
  - [ Get Conversation ](#get-conversations)
  - [ Get Messages ](#get-messages)
  - [ Get Threads ](#get-message-threads)
  - [ Get Members ](#get-members)
  - [ User Search ](#user-search)
  - [ Logout ](#logout)

## Getting Started

Install this package from pypi

```
$ pip install lpulive
$ python
>>> from lpulive import User
>>>
```

## Methods

## `See all Methods`

---

### Get Conversations

- To get all the active chat
- function takes no argument
- function return a `dictionary` object
  - `chats` : list of all the chat active on users profile
    - `id` : id of particular chat
    - `chat_name` : name of the chat
    - `date_time` : last acitve message on that chat
    - `unread` : total unread messages on that chat
  - `total_chat` : total group/private chat active on users profiles

#### Usage

```python
from lpulive import User

regno = < Registration Number >
password = < Password >

user = User(registration_no=regno, password=password)
conversation_data = user.get_conversations()
print(conversation_data)
```

---

### Get Messages

- To get all the messages of selected chat
  - functions takes to argument chat_id, msg_thread
    - `chat_id` : to select a particular chat to get all messages [ required argument ]
    - `msg_thread` : to turn on thread, this will also include the threads of messages ( if applicable ) [ default value is `False` ]
  - function return a `dictionary` object
    - `chat_id`: id of the chat
    - `messages` : list of all the messages in that chat
      - `id` : id number ( smaller the id newer the message )
      - `m_id` : message id
      - `message` : text message
      - `from_user` : message sender name
      - `regno` : message sender registration number
      - `attachment` : any attachment in that message ( if applicable )
      - `thread_message` : get all the thread of a particular message ( if `msg_thread` is `True` )
    - `chat_name` : name of the chat
    - `total_messages` : total messages in that chat
    - `user_name` : name of current user

#### Usage Without threads active

```python
from lpulive import User

regno = < Registration Number >
password = < Password >

user = User(registration_no=regno, password=password)
chat_id = < chat id to search >
messages_data = user.get_messages(chat_id=chat_id)
print(messages_data)
```

#### Usage With threads active

- With threads active fetched messages will also have thread messages
  - with active thread, data fetching may be little slow

```python
messages_data = user.get_messages(chat_id=chat_id,msg_thread=True)
print(messages_data)
```

---

### Get Message Threads

- To get the thread of particular message
  - function takes to parameter `chat_id`, `msg_id`
    - `chat_id` : chat_id of the chat
    - `msg_id` : message id for which thread is to be extracted
  - Function returns a `dictionary` object of thread message of that message
    - `chat_id` : chat_id of the chat
    - `msg_id` : message id of the chat
    - `messages` : messages of all the thread
    - `total_thread` : count of total messages in thread

#### Usage

```python
from lpulive import User

regno = < Registration Number >
password = < Password >

user = User(registration_no=regno, password=password)
chat_id = < chat_id to search >
msg_id = < m_id of a message to see the thread >
threads_data = user.get_message_threads(chat_id=chat_id,msg_id=msg_id)
print(threads_data)
```

---

### Get Members

- To get all the members list in a particular channel
  - function takes one argument `chat_id`
    - `chat_id` : chat_id of the chat
  - function returns a `dictionary` object
    - `chat_id` : chat_id of the chat
    - `members` : list of members
      - `name` : name of the member
      - `regno` : registration number
      - `profile_img` : profile image of the member
      - `phone` : phone number ( if available )
    - `total_members` : count fof total members

#### Usage

```python
from lpulive import User

regno = < Registration Number >
password = < Password >

user = User(registration_no=regno, password=password)
chat_id = < chat id to search >
members_data = user.get_chat_members(chat_id=chat_id)
print(members_data)
```

---

### User Search

- To search user
- function takes one argument `query`
  - `query` : search query
- function returns a `dictionary` object
  - `search_query` : search query
  - `users` : list of users found
    - `id` : id
    - `name` : name of the user
    - `regno` : registration number of the user
    - `department` : department/batch of the user
    - `profile_img` : profile image of the user
  - `total_found` : total user matched the query

#### Usage

```python
from lpulive import User

regno = < Registration Number >
password = < Password >

user = User(registration_no=regno, password=password)
query = < search query >
search_data = user.search_users(query=query)
print(search_data)
```

---

### Logout

- Logout the user from local session
  - Clears up all the local cache
- function takes no argument
- function return a `string` object

#### Usage

```python
from lpulive import User

regno = < Registration Number >
password = < Password >

user = User(registration_no=regno, password=password)
logout_output=user.logout()
print(logout_output)
```

---

Made with 💜 in India
