## EventListener is not defined
[PCF Component Tutorial issue](https://powerusers.microsoft.com/t5/Power-Apps-Pro-Dev-ISV/PCF-Component-Tutorial-issue/td-p/1907421)
```bash
error  'EventListenerOrEventListenerObject' is not defined  no-undef
```
### Follow Steps
1. remove or comment variable declaration buttonClickHandler i.e. 
    
    // private buttonClickHandler: EventListener;
2. remove or comment the statement in methhod "init".  
    
    //this.buttonClickHandler = this.buttonClick.bind(this);

    and add statement 
    
    this.buttonClick = this.buttonClick.bind(this);
3. Update method "init" to add event listener instead with variable this.buttonClickHandler to this.buttonClick  i.e. 
    
    button.addEventListener("click", this.buttonClick);
4. update method "destroy" to remove event listener i.e. 
    this.container.querySelector("button")!.removeEventListener("click", this.buttonClick);

#### Add a comment at the end of your code to skip the eslint check
```ts
private myButtonHandler: EventListener; // eslint-disable-line
```