Component callback functions can be bound to HTML events  
Last time we saw how to create React components, including their properties and state.  
**But the whole point of React is that the component can react to user events.**

In this lesson, we'll see three examples in which the React component's appearance changes based on what's happening in the application.

The state of the component typically changes in response to some user action or event, and we can bind an event to a call back function within the React component.

That component can then change its state using the **setState** function, and when setState is called, that will **automatically call render**, which will redraw the component, and any other affected component in the virtual DOM.

##### Example1

![](/assets/Screen Shot 2018-02-24 at 2.27.44 PM.png)  
We'll start with the classic example of the button that when you click it, it increments some counter.  
We've seen this example a few times already, but now we'll see it in React and then talk about why we'd want to do something like this using a framework like React.

If you remember, as before, I have this button that says, Click Me, and when I click it, the counter increments, and so on.

Let's see how we would do this using a React component.

1. Everything that we saw, the word count, the number of times it's been clicked, and the button are all part of this single component, which I'll call counter.  
2. I'll create the counter component using the ES6 notation of extending React.Component.   
3. The constructor is the function that's called when this component is created. It takes the props that are passed to it and it'll also pass it to the superclass constructor.  
4. Now I'm initializing the state. Remember the state can be initialized in the constructor, and I'm setting the count to zero.   
5. Now I have the callback function incrementCount. In incrementCount, I'm going to use this.setState. This.setState takes an object, which is the new state of this component. Here we're updating the count property of the state by reading the old count and incrementing it by one.  
      **Note:**  
      It's so important to note that you should always only use this.state in the constructor. Any other time you want to modify the state, you should always, always, always use this.setState and then pass it the new state.  
      Two reasons for doing this one

   1. is that this.setState will do an incremental adjustment to the state, as we'll see later if I update one part of the state but not other, setState will handle that.
   2. Also, when I call this.setState, it will automatically call render, because when I set the state or change the state of this component, I may want to redraw it.

6. Our render function is going to return the jsx, which is the HTML of how we want this to appear in our page. Whatever is returned by the render function always has to have some start and end tag. We can't just have text or HTML, there needs to be surrounding HTML element, here we're using a div.

7. Then we'll have the text count, and then we want to show the number of times this button has been clicked. So we'll use the count property from the state, using this.state.count.
8. Now we have the button. We need to bind, or associate, or link some function with clicking the button.

   1. So we set the buttons onClick attributes like this. So this notation is perhaps a little bit clunky, but all it's doing is connecting the incrementCount function from this component to this button.

      So we'll just use this syntax to indicate that the incrementCount function is bound to this action, which is onClick.

9. Last we have the text that appears in the button, which is increment. So we've seen that example a few times now. We've seen how to do it using the dom, we've how to do it using jquery, and we've seen how to do it using React.

###### why would I use React for something like that

it seems like a lot of work to create the component, to use JSX, etc.  
But the main point of React is I can **use these components in different webpages, and that each component maintains its own state** as we'll see in example2.

##### Eample2

![](/assets/Screen Shot 2018-02-24 at 2.28.26 PM.png)

![](/assets/Screen Shot 2018-02-24 at 2.29.00 PM.png)

1. Here we have two like button. These are both the same component, and they both maintain their own state.

   1. When I click the first one at the top, it changes that component so that the text which read Java is now bold and red, and you can also see that the word like switched to unlike.
   2. If I move the mouse down to where it says JavaScript, and I click on that one, now JavaScript will change to red and bold. That, of course, does not affect the other component, and then I can move back, and I can, unlike Java, and each has its own state and renders itself accordingly.

2. Let's start with _how did I drop these components into the HTML_, and then we'll see _the definition of the components_.

   1. I have ReactDOM.render. Remember, whatever we render needs to _be surrounded by some HTML element_, here we'll use a div, and now I have _two instances of the LikeButton_.

      The first LikeButton, I pass it the property, which is the name Java, and the second one I passed the property, which is the name JavaScript.

   2. Now here's the definition of our like button component. Like button is a class that extends React.Component. In its constructor we pass the properties to the super class constructor.

      Now we'll initialize the state so that we'll have a variable called liked, which is set to false.

      Then we have the callback function called toggle. The toggle function will toggle, or alternate, or switch the value of the liked variable.

      When this callback function is invoked we'll use this.setState, and we'll set the value of the liked variable to the opposite of whatever it had previously been. If this.state.liked had been false, now liked will be true and vice versa.

      Again, worth pointing out, that after the constructor, we never set the state directly, but rather we use this.setState, and one of the reasons for doing that, is because it will automatically call render, which will allow us to re-render or redraw this component within the HTML.

      Now, render is a function just like any other function and it can have local variables. So we'll have a local variable called name, which will be set to the name part of the props that was initialized when this component was created,

      and we'll also have a variable called text, which is the text to appear to the right of the thumbs-up sign.  
      Here we're using the ternary operator that you've probably seen before. It'll read the value of liked, and if it's true, then it'll set the text to Unlike, because it's already liked, then we have the opportunity to unlike it.  
      But if liked is false then it will set the text to Like. We can have a local variable called myColor, which will be red if this is liked and black if it's not, and weight, which will be bold if it's liked and normal if not.

      Now we have the return value of the render function, and we'll start out with this span, which will be the name that was passed to it when this object or component was created.  
      We can specify the style or appearance of the text in this span using the style attribute, and passing it an object that contains the key-value pairs, or the properties, for how we want it to appear.  
      Color is the attribute, and we'll set the value to myColor, which was set up here as either red or black. FontWeight is the other attribute. Here we have to use the camel caps style of writing fontWeight, with a capital W here, and we'll set it to weight, which was defined up here as either bold or normal.

      Next we have the name, which was set up here to this.props.name. Next to that will be another span where we'll set the callback function forthe onClick event, and as we saw before we need to use this notation, or this syntax to bind the toggle function to this event. That would be the toggle function up here which will toggle, or switch the value of light.  
      The text within that span includes this, which is the unicode value for the thumbs up icon, and then next to that will be the text which we setup here as unlike or like.

##### Example3

![](/assets/Screen Shot 2018-02-24 at 2.30.15 PM.png)  
![](/assets/Screen Shot 2018-02-24 at 2.30.54 PM.png)

In this last example, we'll see that we can have multiple callback functions for the same component.

I have some text that reads look at me, and when I mouse over it, it'll turn bold, and when I mouse away from it, it'll go back to normal, but then when I move up, and click it, it will turn red. So this component will be called MyText, as always, we'll take the props and the constructor, and then we'll initialize the state.

1. The state will have two values. The first is bold, which indicates whether this should be bold. We'll initialize that to false, and in the color, which we'll initialize to black.

2. Below we have the three callback functions.  
      1. The first one I've called handleMouseOver which will be called when we mouse over this component, and in handleMouseOver I'll set the state so that bold is now true.

   Now keep in mind, as I mention numerous times before, we should always use setState, and not directly change the state. One of the reasons is that when we set the state we want it to automatically call render, but the other part is that we don't want to have to reset the color to black.

   By just setting state for bold true, we will only change that part of the state, and we don't have to keep track of all of the other parts of the state.

   1. I'll have another callback function, for when we move away from the text. I'll call that handleMouseOut, and in this case, I'll set the bold part of the state to be false,

   2. and then last, I'll have a third callback function handleClick. This will be of course called when they click on the text, and rather than using the ternary operator, I'll just use a if else statement. Color is currently red, then I'll change the color to black in the state. Otherwise, if it's not red, then I'll change the color to red.

   3. Now we'll see the render function. The render function is going to create two local variables.

      One is called myColor, which comes from the state, and the other is called weight, which we'll use the bold part of the state, which is true or false. If it's true weight will be bold, if it's false weight will be normal.

      So then we have the return value for render which will be the span. As we saw on the previous example, we can set the style attribute for the span using some object.   
      Here we're setting color to be myColor, and fontWeight to be weight.   
      Then I'll set the onClick attribute of this span, so it will bind the handleClick function, as we saw in the previous slide, to this event, onClick. Likewise, we'll bind handleMouseOver to the onMouseOver event, and we'll bind handleMouseOut to the onMouseOut event.

      Last the text that will appear will come from the props and that's going to be set down at the bottom where I call ReactDOM.render and pass the text as a property to this component when it gets created.

In this lesson we've seen how we can bind user events in HTML elements to the different callback functions in React components, and most importantly, we've seen that invoking the React component's setState function will not only change its state but automatically call render, thus redrawing the component.

