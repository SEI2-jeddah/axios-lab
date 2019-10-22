# Axios

We will be using Axios for our AJAX requests.  Axios is a very popular library and we can use it in the browser and with node.

## Installing

Using npm:

```bash
$ npm install axios
```


Using cdn:

```html
<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
```

### Request
- method
    - GET
    - POST
    - DELETE
    - PATCH/PUT
- url
    - https://swapi.co/api/people/1
    - https://pokeapi.co/api/v2/pokemon/2
- data (optional)

*Get Request Example*
```js
axios({
  method: 'get',
  url: 'https://swapi.co/api/people/1'
});
```

*Post Request Example*
```js
axios({
  method: 'post',
  url: 'https://swapi.co/api/people/1',
  data: {
    firstName: 'brunos',
    lastName: 'ilovenodejs'
  }
});
```

### Response Object

- *data*: the payload returned from the server. By default, Axios expects JSON and will parse this back into a JavaScript object for you.
- *status*: the HTTP code returned from the server.
- *statusText*: the HTTP status message returned by the server.

### Error Object

- *message*: the error message text.
- *response*: the response object (if received) as described in the previous section.
- *request*: the actual XMLHttpRequest object (when running in a browser).

### Handling Responses

Since an AJAX call is asynchronous, we need to handle its response in a particular way.  

You may have already used some asynchronous javascript with `setTimeout()`.  Potentially you ran into a problem with it.  

[Let's take a look at how asynchronous javascript works!](https://www.youtube.com/watch?v=8aGhZQkoFbQ)

To work with asynchronous javascript, we are going to use promises and a promise chain.

```js
// Example 1
axios({
  url: 'https://dog.ceo/api/breed/boxer/images/random',
  method: 'get',
}).then().catch() // .then and .catch are chained at the end of the request 
```

It is easier to ready if we place them on the next line
```js
axios({
  url: 'https://dog.ceo/api/breed/boxer/images/random',
  method: 'get',
})
.then() // .then wants a function to run if the request is succesful
.catch() // .catch wants a function to run if the request is fails
```

The `.then` and `.catch` method want us to pass them functions to run.
`.then` wants a function to run if the request succeeds 
`.catch` wants a function to run if the request fails
```js
axios({
  url: 'https://dog.ceo/api/breed/boxer/images/random',
  method: 'get',
})
.then(doGoodStuff) 
.catch(doErrorStuff) 
```

We often use anonymous, fat arrow functions.
```js
axios({
  url: 'https://dog.ceo/api/breed/boxer/images/random',
  method: 'get',
})
.then(() => {
    // code for if the request succeeds
}) 
.catch(()=>{
    // code for if the request fails
}) 
```

`axios` will pass our functions the `response` or `error` object so that we can access the data that the API returns to us.
```js
axios({
  url: 'https://dog.ceo/api/breed/boxer/images/random',
  method: 'get',
})
.then((response) => {
    // code for if the request succeeds
    console.log(response)
}) 
.catch((error)=>{
    // code for if the request fails
    console.log(error)
}) 
```






# Labs

### Star Wars

- [Star Wars API](https://swapi.co/)

1.  On page load, make an AJAX call to get the data for film 1 an add the following data to the page
- title
- release_date 
- episode id
- opening_crawl
- director
- producer

### Pokemon

- [Pokemon API](https://pokeapi.co/)

1.  On page load, make an AJAX call to get pikachu data and display the following data on the page
- name
- height
- weight
- sprites front_default as image
- moves as list of names
- ability as list of names

### Dogs

- [Dog API](https://dog.ceo/dog-api/)

1.  On page load, make an AJAX call to display a random dog image on the page.
2.  On page load, make an AJAX call to list all the dog breeds on the page.

Challenge
- Make each dog breed clickable and on click display all dog images for that breed.

### GOT

- [Game of Thrones API](https://anapioficeandfire.com/)

Research the data on your own and use it how you'd like!
