# Server Side rendering in Next JS

When we use react to develop our website (NOT using frameworks like NextJS), the entire bundle of our code gets delivered
to the user when they come to our website.

This may be okay for websites with a small bundle size as it will take relatively short time for the website to load.
However, the problem arises when websites come with large code bundles. This will mean that the user will have to wait
for the website to load that large code bundle, which will take quite long. Not only will this increase the loading time
for the users, it will lower the overall UX.

To solve this, Next JS implements SSR for their apps. When a user enters a website (let's say the landing page), that
individual page is going to get built. Notice I said "individual" as Next JS loads pages individually. Learn more about
how Next JS splits code in their app [here](https://nextjs.org/learn/foundations/how-nextjs-works/code-splitting).

</br>For example, let't say that we have an app that loads a list of data (list of vegetables perhaps?) and shows it to
our users.

```jsx
// pages/index.js

export default functions Home(){
  const [veggies, setVeggies] = useState([]);
  
  useEffect(() => {
    const fetchTodos = async () => {
      const res = await fetch("URL that will fetch data");
      const data = await res.json();
      setTodos(data);
    };
    fetchTodos();
  }, [])
  
  return (
    {todos.length === 0 ? (
      <div>Loading...</div>
    ) : (
      veggies.map((veggie, i) => (
        <div key={i}>
          <p>
            {veggie.name}: {veggie.desc}
          </p>
        </div>
      ))
    )
  )
}
```

Let's run the server and see what happens. What can we see? Well, we can see a list of vegetables and the description
for each one of them. However, before the list appears on screen, we can see (for a very brief second) the text "Loading...".
Now of course the "Loading..." text is just an exemplary representation of what we would see if there's a loading page.
For this simple app, it's only one-fourth of a second. However, in real-life projects, it could maybe take up to a few seconds (or more).

