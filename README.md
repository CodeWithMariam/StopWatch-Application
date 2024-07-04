# Stopwatch Application

This project is a simple stopwatch application that allows users to start, stop, and reset a timer. The stopwatch displays the elapsed time in hours, minutes, and seconds, updating every second using JavaScript.

## Features
- Displays elapsed time in hours, minutes, and seconds.
- Start button to begin the stopwatch.
- Stop button to pause the stopwatch.
- Reset button to clear the stopwatch and reset the time to 00:00:00.

## How It Works
The JavaScript code uses the `setInterval` function to update the time every second. The `clearInterval` function is used to stop the timer. The display is updated dynamically to show the elapsed time in the format HH:MM:SS.

## Code Explanation
```javascript
let [seconds, minutes, hours] = [0, 0, 0];
let displayTime = document.getElementById("displayTime");
let timer = null;

function stopwatch() {
    seconds++;
    if (seconds == 60) {
        seconds = 0;
        minutes++;
        if (minutes == 60) {
            minutes = 0;
            hours++;
        }
    }

    let h = hours < 10 ? "0" + hours : hours;
    let m = minutes < 10 ? "0" + minutes : minutes;
    let s = seconds < 10 ? "0" + seconds : seconds;

    displayTime.innerHTML = h + ":" + m + ":" + s;
}

function watchStart() {
    if (timer !== null) {
        clearInterval(timer);
    }
    timer = setInterval(stopwatch, 1000);
}

function watchStop() {
    clearInterval(timer);
}

function watchReset() {
    clearInterval(timer);
    [seconds, minutes, hours] = [0, 0, 0];
    displayTime.innerHTML = "00:00:00";
}
```
## Explanation
The stopwatch function increments the time by one second every time it is called. When seconds reach 60, they are reset to 0, and minutes are incremented. Similarly, when minutes reach 60, they are reset to 0, and hours are incremented. The time is displayed in a two-digit format using the ternary operator.

The watchStart function starts the timer using `setInterval` and ensures that any previously running timer is cleared using `clearInterval`. The watchStop function pauses the timer by clearing the interval. The ``watchReset`` function stops the timer and resets the time to 00:00:00.

##  Contributing
If you'd like to contribute to this project, please fork the repository and submit a pull request.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Additional Resources
Here are some articles that might help you understand the concepts used in this project:

- [JavaScript setInterval](https://developer.mozilla.org/en-US/docs/Web/API/setInterval)
- [JavaScript clearInterval](https://developer.mozilla.org/en-US/docs/Web/API/clearInterval)
- [JavaScript Date Object](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)
