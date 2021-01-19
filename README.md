# Typing Speed Game #
Typing game built with Javascript. The timer will start counting once user types in the first character in the textarea. 

### Running Timer Explained ###
1. The timer is a variable with int data type
1. The timer value is stored in an array `[0,0,0,0]` or [hh:mm:ss:ms]
1. setInterval() method increments the timer[3] variable every 10/1000 secs. 
```javascript    
    // Minutes: (milliseconds/100) / 60 
    // Note: 1 sec = 1000 ms, but since we increment every 10ms, we only / 100
    timer[0] = Math.floor((timer[3]/100)/60)

    // Seconds: Same formula as above, but deduct the minutes
    timer[1] = Math.floor((timer[3]/100) - (timer[0] * 60))

    // Milliseconds: Deduct the values from mins and seconds
    timer[2] = Math.floor(timer[3] - (timer[1] * 100) - (timer[0] * 6000)); 

    // Arrray[3] is not displayed
```

### Starting / Stopping setInterval from different functions ###
We initialize the variable `var interval` to store the setInterval() method. This allows us to access the method outside our original function. 

To start the timer: 
```javascript 
const start = () => {
    if (textEnteredLength === 0 && !timerRunning) {
        interval = setInterval(runTimer, 10);
    }
}
```

To end the timer: 
```javascript 
const reset = () => {
    clearInterval(interval); 
    interval = null; // releases the memory so we can reassign at same index
}
```


