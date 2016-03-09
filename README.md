## HTTP Questions

__URLs__

* Name all of the parts of the url that you can remember.  In your own words describe what they do.
	* **protocol** - the protocol is the standard rules that browsers and servers use to communicate with one another. `http://` and `https://` are almost universal (at least among broswers, 
	
	* **domain** - the domain is the root page for whatever website you are trying to access. It defines control over all the content and activity within that website, and is registered in the Domain Name System (DNS). The domain corresponds to a unique IP address (or addresses), but domain names are far easier for humans to remember and thus access in their browsers.
	
	* **port** - A port number is always required, but rarely declared in URLs. It comes right after the domain and is set depending on the protocol and domain. Most times it is not lsited in the URL, and generally if the protocol is `http://` the port is `80`, and if its `https://` the port is usually `443`.
	
	* **path** - The path is the specific location of the page/information you are trying to access within the greater domain. Similar to within your file system on your personal computer, the path is like a map that dives deeper into the website's folders to find more specific content. 
	
	* **query string** - The query string allows the user to provide further specification of the content they are looking for, by adding extra parameteres. For instance in a Google search, if you specify that you are only looking for images within a certain height and width, the query string will inform the server that it should only provide certain responses when sending back data for the page.
	
	* **anchor tag** - The anchor tag is used to specify what specific part of a single webpage the user wants to be directed to immediately. Especially on single pages that have a large number of sections with a lot of scrolling involved, the anchor tags can be used to more easily navigate along the page (by "jumping to" a specific section.
	
* Name the pieces of the following urls:
	* `https://www.google.com/`
	
	**
	protocol:`https://`
	domain: `www.google.com/`
	**
	
	* `https://workbook.galvanize.com/cohorts/41/learning_experiences/367`
	
	**
	protocol:`https://`
	domain:`workbook.galvanize.com`
	path:`cohorts/41/learning_experiences/367`
	**
	
	* `http://locahost:5000/animals/puppies?onlycute=1&size=medium#firstpuppy`
	
	**
	protocol:`http://`
	domain:`locahost:5000`
	path:`/animals/puppies`
	query string: `?onlycute=1&size=medium`
	anchor tag: `#firstpuppy`
	**
	
	* `https://en.wikipedia.org/wiki/List_of_HTTP_status_codes#4xx_Client_Error`
	
		**
	protocol:`https://`
	domain:`en.wikipedia.org`
	path:`/wiki/List_of_HTTP_status_codes`
	anchor tag: `#4xx_Client_Error`
	**
	
* Can a server use more than 1 port?

```
Yes it can. I don't feel like I understand this very well, but your computer (which can be a server) can use multiple ports. For instance, you can concurrently open multiple websites locally using different ports  (like localhost:5000 and localhost:3000). Certain ports are reserved (like 80 and 443 for HTTP and HTTPS requests) and can only be accessed if you have sudo privileges.
```


* Why is https different than http?

```
HTTP stands for Hyper Text Transfer Protocol. HTTPS stands for Hyper Text Transfer Protocol SECURE. The main difference is that with HTTPS, the information passed between the client and server is encrypted so it cannot be hijacked by hackers. Most webiste use a Secure Sockets Layer (SSL) certificate to establish a trusted connection between the client and server. In essence, it is an encryption both ends of the transfer agree upon and are privy to that encrypts the data.
```

* How does a server interpret the following url's query paramter.  What data structure does it create on the server?

```
http://locahost:5000/animals?puppies=fido&puppies=max&puppies=moxie
```

```
The server interprets the query parameter as an array. The name of the array is "puppies" and the elements within the array are "fido", "max" and "moxie".
```


__HTTP Request/Response__

* Name at least 4 http verbs
* What is each verb useful for in your own words

```
GET - Get sends a request from the client to the server asking for some data. For instance, when you enter the URL of a webpage into your browswer, a GET request is sent to that webpage's server, and the HTML file is sent back in response. Importantly, GET requests do NOT change the content of the server.
POST - Post sends information from the client to the server. For instance, when you complete a form to sign up as a new user, when you click 'submit' that information is sent via a POST request to the server. Importantly, POST requests DO change the content of the server (like by creating a new user). 
PUT - Put updates information that is already on the server.
DELETE - Delete is for removing information that currently exists on the server.
```

* What does idempotent mean?

```
Idempotent means that the state of the server does not change when a request is made. So, GET requests are idempotent because when requesting information from the server, no changes are made to the server itself. You can ask for Google to load as many times as you want, and the site's contents won't change. However, POST requests are **not** idempotent, because each time you submit one you are requesting to add new information to the server (like creating a new user). If you continually submit the same POST request, it will be repeated each time.
```

* Name the 5 http status code ranges.  What are they used for in general?

```
1XX - In progress 
2XX - Status Ok
3XX - Redirect, needed to access somewhere else
4XX - Client side error - request was invalid
5XX - Server-side error - something went wrong
```

* If a server returns a http status code of 301 and a location of `https://www.google.com/`, what does the browser do?

```
It means that the URL you requested has moved permanently, and you will be redirected to Google.
```

* For the following HTTP headers, decide if the following header is used for requests, responses or both:
	* Accept
	
	```
	BOTH
	```
	
	* Content-type
		
	```
	RESPONSES
	```
	
	* User-agent
		
	```
	REQUESTS
	```
	
	* Set-cookies
		
	```
	RESPONSES
	```
	
	* Cache-control
		
	```
	BOTH
	```
	
	* Cookie
		
	```
	REQUESTS
	```
	
* Is the following a http request or response?  How do you know for each?

```
HTTP/1.1 200 OK
Access-Control-Allow-Origin: *
Vary: Accept
Content-Type: text/html; charset=utf-8
Content-Length: 722
ETag: W/"2d2-Wu0We9N5g35FXWY+gOATLA"
Date: Tue, 08 Mar 2016 20:37:11 GMT
Connection: keep-alive

<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <link rel="stylesheet" href="/style.css">
    <title>Student Roster</title>
  </head>
  <body>
    <main>
      <h1>Student Roster</h1>
      
        <section>
          <h3>Daenerys Targaryen</h3>
          <span>Student Id: nys8fbohl</span>
          <h4>Hobby: Motherhood</h4>
          <img src="https://i.imgur.com/KlycRG5.jpg" alt="Daenerys Targaryen" />
        </section>
      
        <section>
          <h3>Tyrion Lannister</h3>
          <span>Student Id: njehukbohe</span>
          <h4>Hobby: Traveling</h4>
          <img src="https://i.imgur.com/fFMusdC.png" alt="Tyrion Lannister" />
        </section>
      
    </main>
  </body>
</html>
```

```
The above is a http response. I know this first because the first line of the header is a status code, which is 200 OK indicating the request went through. Below that the Content Type, Accept and other information is included in the header. Finally the Body contains the HTML document of the webpage that was requested.
```


```
DELETE /students/n1vmyrw3x HTTP/1.1
Host: g22-students.herokuapp.com
Accept: application/json
Cache-Control: no-cache
Postman-Token: 0041e3c3-efdb-f0c3-b2f4-2d79f6d0f44b
```

```
The above is an http request. I first know this because DELETE specifies the request type. It also includes the Host that the request is attempting to contact, what type of content it is expecting (JSON) and information about the cache control.
```

__JSON__

* Describe what JSON is.  What is it used for.

```
JavaScript Object Notation is the defacto structure of content that is exchanged across the web. It is a structure that very easily converts from objects like objects and arrays into a string (using JSON.stringify) that can easily be transmitted across the web, and then can also easily be covnerted back from a string back to objects like objects and arrays (using JSON.parse). 
```

* Convert the following map into a javascript object then console log the age.

```
{ "company" : "Github", "age": 7, "categories" : "Services,Internet,Software"}
```

```
var jsonMap = JSON.parse('{ "company" : "Github", "age": 7, "categories" : "Services,Internet,Software"}');
console.log(jsonMap.age);
// 7
```

* Convert the following to a javascript object.  Console log each company name.

```
{ "Companies":[ { "company": "Github", "age": 7, "categories": "Services,Internet,Software"},
              { "company": "Airbnb", "age": 6, "categories": "Hotels,Travel"},
              { "company": "Square", "age": 7, "categories": "FinTech,Hardware + Software,Finance"},
              { "company": "Dropbox", "age": 11, "categories": "Cloud Data Services,Storage,Web Hosting"}
            ]
}
```

```
var jsonMap2 = JSON.parse('{ "Companies":[ { "company": "Github", "age": 7, "categories": "Services,Internet,Software"},{ "company": "Airbnb", "age": 6, "categories": "Hotels,Travel"},{ "company": "Square", "age": 7, "categories": "FinTech,Hardware + Software,Finance"},{ "company": "Dropbox", "age": 11, "categories": "Cloud Data Services,Storage,Web Hosting"}]}');
for (var i = 0; i<jsonMap2.Companies.length; i++) {
    console.log(jsonMap2.Companies[i].company);
}
```

* The following is javascript.  Convert the object to a string and console log it.

```
var myObj = {
  company: "Galvanize",
  age: 3,
  categories: "Education"
};
```

```
var myObj = {
  company: "Galvanize",
  age: 3,
  categories: "Education"
};

var myJSON = JSON.stringify(myObj);

console.log(myJSON);
// {"company":"Galvanize","age":3,"categories":"Education"}
```

__MISC__

* Describe what DNS is.

```
The DNS stands for the Domain Name System. The DNS is basically the phone book for the internet. Each root domain is registered with the DNS, and the owner of the domain is considered the proprietor of all the content and action that takes place within that domain. The DNS is useful for a few reasons: first, it creates a directory of all the domains, and the IP address that each is associated with. This is important because users will enter domain names into a browser, but to send/receive resquests and responses between clients and servers, the IP address is what HTTP uses. 
```

* In the terminal, type `man curl`.  Look at the man page for curl.  What do the following flags do? `-v`, `-X`.  (Hint: to search for a string, type `/` then the text you want, then enter.  To quit the man page, type `q`).
* What is TCP/IP?  How does it interact with HTTP?
* Does HTTP break the data that is being sent into small packets?  If not, what protocol is responsible for it?
