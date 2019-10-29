# omdb-vue-component

[Open Movie Database](http://www.omdbapi.com) Component for Vue.js

![](https://user-images.githubusercontent.com/2070277/67768583-e90a8d80-fa63-11e9-93fc-a946d62e7e66.png)

Movie list (/src/App.vue)

```javascript
  data() {
    return {
      title: '&#9733; My Favorite Films',
      films: [
        'tt2905772', 
        'tt9418878', 
        'tt5334076', 
        'tt4373956', 
        'tt1827487'
      ],
      currentIndex: 0,
    };
  },
```

Get movie ID from IMDb website

![](https://user-images.githubusercontent.com/2070277/67769649-e90b8d00-fa65-11e9-85a1-d06602a0e755.png)

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
