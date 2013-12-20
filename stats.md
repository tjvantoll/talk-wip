Average site size is 1590KB as of October 2013 (http://httparchive.org/trends.php#bytesTotal&reqTotal)

Average worldwide download speed was 580KB/sec in 2011 (http://mashable.com/2011/09/21/fastest-download-speeds-infographic/). The average US user downloads at 4.93MB/sec. I'll assume both are faster now.

Average mobile RTT time in the US is ~350ms, average download speed is 1.5MB/sec. LTE networks offer RTT times < 100ms and faster download speeds.

All this data shows that minimizing RTT time (by reducing HTTP requests) if far more important than size of the files being downloaded. Which is why all web performance guidelines - including [Google's](https://developers.google.com/speed/docs/best-practices/rules_intro) and [Yahoo's](https://developers.google.com/speed/docs/best-practices/rules_intro) - prioritize minimizing HTTP requests above everything else.



### Are jQuery and jQuery UI Too Big For Mobile?

Answer = yes


Raw data of 5 loads in each browser. Times are in ms.

Browser                 | jQuery 1.10.2            | jQuery 2.0.3 
------------------------|--------------------------|-------------------------
IE 11                   | 18, 20, 20, 20, 24       | 18, 21, 14, 16, 15
Chrome 31               | 20, 8, 6, 5, 7           | 15, 8, 5, 7, 6
Safari 7                | 11, 4, 4, 4, 4           | 9, 5, 3, 3, 2
Firefox 26              | 12, 13, 13, 12, 13       | 12, 12, 11, 12, 12

iOS7 Safari             | 60, 39, 58, 56, 58       | 40, 32, 37. 69, 40
Android 2.2             | 1080, 266, 434, 271, 470 | 928, 264, 494, 315, 220
Android 4.0             | 531, 141, 153, 112, 105  | 453, 106, 104, 145, 148
Chrome 31 (Android 4.4) | 271, 126, 101, 68, 53    | 219, 86, 38, 86, 123




No IE8 because of http://ejohn.org/blog/accuracy-of-javascript-time/

if (window.console && typeof(window.console.time) == "undefined") {
    console.time = function(name, reset){
        if(!name) { return; }
        var time = new Date().getTime();
        if(!console.timeCounters) { console.timeCounters = {}; }
        var key = "KEY" + name.toString();
        if(!reset && console.timeCounters[key]) { return; }
            console.timeCounters[key] = time;
        };

    console.timeEnd = function(name){
        var time = new Date().getTime();
        if(!console.timeCounters) { return; }
        var key = "KEY" + name.toString();
        var timeCounter = console.timeCounters[key];
        var diff;
        if(timeCounter) {
            diff = time - timeCounter;
            var label = name + ": " + diff + "ms";
            document.body.innerHTML += label;
            delete console.timeCounters[key];
        }
        return diff;
    };
}

Also might be handy: http://carlos.bueno.org/2010/02/measuring-javascript-parse-and-load.html