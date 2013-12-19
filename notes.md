* Explain browser utopia

* Disclaimers
	- I'm on the jQuery UI team.
	- This is a jQuery conference

* Haters Gonna hate

* Arguments that jQuery is no longer needed:
	- Native APIs (e.g. querySelectorAll) can do everything now
	- 28k is just too big, especially for mobile
	- Too slow

* DOM APIs / CSS can do everything now

	Traversal hell

	Can't loop
	Chaining is the SHIIIIIT

	- Show of hands - who could code an XMLHttpRequest

	Gotchas
		- DOM methods that return Live NodeLists: getElementsByTagName, getElementsByClassName
		- slicing every NodeList and caching its length before iterating (it's real slow and bad if you don’t)
		- forEach
		- querySelectorAll mess
		- firstElementChild: http://jsfiddle.net/j3bfz/



* Too big / bloated (file size)
	- <script>: Download and parsing
		- Download speeds actually aren't bad, even on mobile
		- Single biggest problem is latency.
			- If you have JavaScript and you're concerned about performance you should have one <script> tag in the body.
			- DO NOT LOAD JQUERY FROM A CDN!!!!!!!
			- Size isn't all that important when downloading

	one less jpeg



	- Do not load all of jQuery UI!!!!
	- Do not load all of jQuery Mobile!!!
	- Size really isn't that important.

	- Parsing is
		- Stats

	- AMD


* Too slow

	http://www.leebrimelow.com/native-methods-jquery/
	"Remember, jQuery is an amazing library that makes all of our lives easier. But you should always choose to use native DOM methods if they are available to you."

	- Animations

	- http://jsperf.com/zepto-1-0-1-vs-jquery-2-0-3-2013-08-08

	- Never prematurely optimize
		Premature optimization is the root of all evil -- DonaldKnuth

	- Show how slide up is so much easier.



Various pro arguments that I'm not sure where to put.
	- Clean APIs
	- Google-ability
	- Speed of getting things done ("write less, do more")

What you should do:
	- Concat scripts
	- Minify
	- gzip


