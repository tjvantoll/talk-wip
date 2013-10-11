Average site size is 1590KB as of October 2013 (http://httparchive.org/trends.php#bytesTotal&reqTotal)

Average worldwide download speed was 580KB/sec in 2011 (http://mashable.com/2011/09/21/fastest-download-speeds-infographic/). The average US user downloads at 4.93MB/sec. I'll assume both are faster now.

Average mobile RTT time in the US is ~350ms, average download speed is 1.5MB/sec. LTE networks offer RTT times < 100ms and faster download speeds.

All this data shows that minimizing RTT time (by reducing HTTP requests) if far more important than size of the files being downloaded. Which is why all web performance guidelines - including [Google's](https://developers.google.com/speed/docs/best-practices/rules_intro) and [Yahoo's](https://developers.google.com/speed/docs/best-practices/rules_intro) - prioritize minimizing HTTP requests above everything else.



### Are jQuery and jQuery UI Too Big For Mobile?

Answer = yes


Browser          | Core 1.10.2 | UI 1.10.3 | Core 2.0.3 | jQuery UI Slider + Dependencies |
-----------------|-------------|-----------|------------|---------------------------------|
IE10             | 26          | 58        | 27         | 10                              |
Chrome 30        | 18          | 36        | 16         | 7                               |
Safari 6         | 12          | 23        | 12         | 5                               |
Firefox 24       | 11          | 19        | 10         | 5                               |
iOS7 Safari      | 46          | 115       | 39         | 11                              |
Android 2.3      | 169         | 202       | 142        | 35                              |
Chrome (Android) | 78          | 107       | 74         | 21                              |

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