What are the characteristics of setTimeout, setInterval and requestAnimationFrame? 

Timers are certainly essential for asynchronous programming. Common timer functions include setTimeout, setInterval, and requestAnimationFrame. The most commonly used is setTimeout, and many people believe that the delay specified in setTimeout dictates exactly when the function will execute.

In fact, this view is wrong, because JS is executed on a single thread. If the previous code affects the performance, it may result in setTimeout not executed as schedule. Of course, setTimeout can be adjusted by code to make the timer relatively more accurate.

Now let's look at 'setInterval' . This function is basically the same as setTimeout, except that it executes a callback function at regular time intervals. 

Generally, it is not recommended to use 'setInterval'. Firstly, similar to setTimeout, it cannot guarantee that the task will be executed exactly at the scheduled time. Secondly, it has an issue of execution accumulation.  See the following pseudo code.
function demo() {
  setInterval(function(){
    console.log(2)
  },1000)
  sleep(2000)
}
demo()

In the browser environment, if a time-consuming operation occurs during timer execution, multiple callback functions may execute simultaneously once the operation is completed, potentially leading to performance issues. 

If a looping timer is needed, it can effectively be implemented using 'requestAnimationFrame'.

With its intrinsic throttling feature, 'requestAnimationFrame' can largely ensure only one execution within 16.6 milliseconds, provided that there are no frame drop issues. Moreover, this function's delay effect is highly accurate, without the common timing issues of other timers, and it can also be used to serve the purpose of setTimeout.