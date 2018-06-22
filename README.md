# TCP Chatroom

##  Documentation  
required node dependencies:
```
npm i uuid
npm i netcat
npm i winston
```

use `require()` to include the chatroom in your project and start the server
`require('./lib/chatroom');`

connect to the server using netcat: `nc <server> <port>`
```
nc localhost 3000
```

the following commands are supported:
```
@list // lists the nicknames of all users in the chatroom

@nickname myNickname // changes your nickname to 'myNickname'
@nickname coolUser123 // changes your nickname to 'coolUser123'

@all message // broadcasts 'mesage' to all users
@all hello world // broads 'hello world' to all users

@dm targerUser message // direct message to targetUser with the included message
@dm coolUser123 hello world // coolUser123 will receive the message 'hello world'
```
