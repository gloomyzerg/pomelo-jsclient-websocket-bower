#Pomelo javascript websocket client

The javascript websocket client library for [Pomelo](https://github.com/NetEase/pomelo).

Since there are two kind connectors in pomelo 0.3, socket.io and socket(websocket), we provide two javascript clients for different usage.
[websocket client](https://github.com/gloomyzerg/pomelo-jsclient-websocket-bower) is optimized for data transfer size, the package is compressedin high rate. It's suitable for HTML5 online game, especially mobile platform.

[socket.io client](https://github.com/gloomyzerg/pomelo-jsclient-socket.io-bower) is excellent for browser compatibility, the package is in json. It's suitable for online realtime application on browser, like chat, on which browser compatiblity is an important issue.

The apis are almost the same in both clients, except websocket client need a handshake callback for protocol data.
Both clients use [bower](https://github.com/bower/bower) package manager for building.

##Usage

### connect to the server
``` javascript
  pomelo.init(params, callback);
```  
params object are 

example:
``` javascript
  pomelo.init({
    host: host,
    port: port,
    user: {},
    handshakeCallback : function(){}
  }, function() {
    console.log('success');
  });
```

user field is user define json content  
handshakeCallback field is handshake callback function  

### send request to server with callback
``` javascript
  pomelo.request(route, msg, callback);
```

example:
``` javascript
	pomelo.request(route, {
		rid: rid
	}, function(data) {  
    console.log(dta);	
	});
```

### send request to server without callback
``` javascript
  pomelo.notify(route, params);
```

### receive message from server 
``` javascript
  pomelo.on(route, callback); 
```

example: 
``` javascript
	pomelo.on('onChat', function(data) {
		addMessage(data.from, data.target, data.msg);
		$("#chatHistory").show();
	});
```

### disconnect from server  
``` javascript
pomelo.disconnect();
```  
