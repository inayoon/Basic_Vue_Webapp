# Basic Vue Web-App

### - Mini Vue Website. 
 
## All Studios for Rent in Seoul

### `Home` Page

 <img src="https://user-images.githubusercontent.com/100747899/190060596-31f08133-cb55-4320-a086-273826e37574.gif">
 
 - created all the studios with Card components and properly data-binding
 - used v-for and v-if to show up the Card components and a Discount component
 - created routes using react-router-dom library
 - made an ajax call using Axios library to load more items
 - plus, catch statement to handle the error  
           
```JavaScript

       <button onClick={()=>{
            axios.get('https://codingapple1.github.io/shop/data2.json')
            .then((result)=>{ 
              console.log(result.data) 
              let copy = [...shoes, ...result.data];
              setShoes(copy);
            })
            .catch(()=>{
              console.log('Failed to get data')
            })
          }}>More</button>
```
  
### `Detail` Page

<img src="https://user-images.githubusercontent.com/100747899/190066376-3fec7020-822f-437c-aa36-74964da9174f.gif">

 - used Lifecycle hook using useEffect
 - found out codes inside the useEffect run after html rendering
 - So, some codes that takes time should be insdie of the useEffect Hook 
 - used setTimeout function insdie of the useEffect Hook to prompt modal for 3 sec  

```JavaScript


  useEffect(() => {
    let a = setTimeout(() =>{ setAlert(false)},3000)
    return () => 
      clearTimeout(a) 
    })
```
