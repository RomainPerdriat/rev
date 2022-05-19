# Faire des requetes Ajax avec axios

On commence par faire un `yarn add axios`

ensuite :
 ```js


import axios from 'axios';

axios({
  url: '/posts',
  method: 'GET',
  baseURL: 'https://oclock-open-apis.vercel.app/api/blog';
})
  .then((response) => {
    console.log('reponse :', response);
  })
  .catch((error) => {
    console.error('error :', error);
  })
```

ou plus simplement : 
```js

export async function requestBlogArticle() {
  try {
    const response = await axios.get('https://oclock-open-apis.vercel.app/api/blog/posts');
    return response;
  }
  catch (err) {
    return err.response;
  }
}
```