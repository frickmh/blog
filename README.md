# blog

Mark's Blog

11-3-2017

Problems with Copying and Pasting Functions in Node Modules

Since I'm still pretty new to Node, I copied and pasted a bunch of common functions that I was using across my node modules, instead of creating a seperate module for the common function.

It seemed innocent enough, but my server started acting up.  Sometimes everything would work great, but usually I'd get a 504 error.  Determined to get to the root of it, I tried logging the function names, and to my horror, started getting values from a completely different module!

After puzzling for a while about what could be wrong (and searching unsuccessfully on how to fix random 500 errors), I found that I named one of my functions for getting web data 'httpGet' in several of my modules!  Thus, the 'httpGet' function was being assigned several times in the same Node kernel!  The value would be different every time because there was a race condition!

So my 'messy' solution was to just rename my 'httpGet' function to a more specific name.  However, in the future I'll want to create a 'httpGet' module and import it into my other modules to avoid this problem.

That's it for my first blog article!  Hopefully I'll be back soon to write more!
