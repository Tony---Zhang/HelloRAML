##1. ENTER ROOT
* ####Basic information in text editor

* ####With extension `.raml`
   
* ####Root: apply to the rest of your API
	
```
#%RAML 0.8
---
title: e-BookMobile API
baseUri: http://api.e-bookmobile.com/{version}
version: v1
```
  
##2. ENTER RESOURCES
* ####Resources all begin with a slash `(/)`
	
```
/users:
  /authors:
  /books:
```
#####_Each of these resources is a collection of individual objects._
 
* ####Define some sub-resources

```
/authors:
  /{authorname}
```
      
##3. ENTER METHODS
* ####GET, PUT, POST, DELETE(`lower case`)

```
/books: 
  get: 
  post:
  put:
```

##4. ENTER URI PARAMETERS


```
/books:
  /{bookTitle}
```
      
	/books:
      get:
      put:
      post:
      /{bookTitle}:
        get:
        put:
        delete:
        /author:
          get:
          /publisher:
            get:

##5. ENTER QUERY PARAMETERS
* ####Filtering a collection

```
/books:
  get:
   	queryParameters:
      author:
	  publicationYear:
      rating:
      isbn:
  put:
  post:
```
```
/books:
  /{bookTitle}
    put:
      queryParameters:
        access_token:
          displayName: Access Token
          type: string
          description: Token giving you permission to make call
          required: true
```              
`http://api.e-bookmobile.com/books/Stiff?access_token='ACCESS TOKEN'`

##6. ENTER RESPONSES
```
/books:
  /{bookTitle}:
    get:
      description: Retrieve a specific book title
      responses:
        200:
          body:
            application/json:
              example: |
                {
                  "data": {
                    "id": "SbBGk",
                    "title": "Stiff: The Curious Lives of Human Cadavers",
                    "description": null,
                    "datetime": 1341533193,
                    "genre": "science",
                    "author": "Mary Roach",
                    "link": "http://e-bookmobile.com/books/Stiff",
                  },
                  "success": true,
                  "status": 200
                }
```

##_Tool: raml2html_

####1. npm i -g raml2html

####2. raml2html example.raml > example.html
  