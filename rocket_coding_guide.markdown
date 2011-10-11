ROCKET CODING GUIDE
===================



Objective-C
------------

A lot of this is based on the [ZDS Style Guide](http://www.cimgf.com/zds-code-style-guide/)

+ Add -Wall (all warnings) and -Werror (warnings are errors) to the additional flags. This catches a lot of things and keeps the code warning free.

+ Check the 'analyze' option in the projects settings so klang runs during each build.

+ 2 spaces for tabs.

+ Put your @synthesize entries at the top of your .m and and give them a protected instance variable, like @synthesize foo = _foo;. Only define the @property. Don't define _foo in the interface.

+ Put your -dealloc, -viewDidUnload and -cleanup methods at the top of your .m

+ In your cleanup or dealloc, use self.someProperty = nil to free a retained property.

+ If allowed by the project's target runtime, only define your attributes using @property. Meaning, don't duplicate them in the interface definition. This is allowed if deploying on iOS 4+ or 64bit Mac.

+ Use dot notation

+ Do *not* do fancy formatting of methods like:

<pre><code>[pants thisIsMy:fancy
         method:trucks
           isOK:NO];</code></pre>

Instead put it all on one line and let Xcode wrap it for you.

<pre><code>[pants thisIsMy:fancy method:trucks isOK:YES];
</code></pre>

There are exceptions to the above rule: dictionaryWithObjectsAndKeys: should have one line per object and key pair and the trailing nil should also be on its own line. Just use your best judgement here.

+ NSLog should not be used in production projects. An alternative debug logging mechanism should be used. One we can turn off in release builds.

+ If an app is to access NSUserDefaults, it should have an app specific Settings singleton (Google SynthesizeSingleton.h or ask Brian for existing examples). Each setting should have a @property and a custom setter and getter that does the NSUserDefaults talking and synchronizing.

+ Storing items in the keychain (passwords/etc) should also go through a Settings singleton as a property.

+ Projects using Core Data should use mogenerator: https://github.com/rentzsch/mogenerator

+ Projects using Core Data should use Active Record Fetching For Core Data: https://github.com/magicalpanda/activerecord-fetching-for-core-data

+ Projects using Core Data should consider having all the NSPredicate fetching and all defined in the mogenerate'd models instead of scattering them all about. So add methods like: 

<pre><code>+ (NSArray *) allInGallery:(GGallery *)aGallery</code></pre>

and let that method do the Active Record for Core Data fetch.

+ Projects using Core Data should use NSFetchedResultsController when appropriate.

+ Projects accessing the internets should use ASIHTTPRequest and SBJSON where appropriate: http://allseeing-i.com/ASIHTTPRequest/

+ Projects should consider using https://github.com/mikeash/MACollectionUtilities

+ MBProgressHUD should be used for modal spinners: https://github.com/jdg/MBProgressHUD

+ Direct use of the GCD API's should be reserved for very specific cases that need it. Instead, prefer NSOperation &amp; NSOperationQueue, which will use GCD behind the scenes for free.

+ Run your main debug scheme with the argument "NSZombieEnabled" "YES" 


Git
---

+ All production projects should be stored on madebyrocket's github account

+ git submodule's should *not* be used unless it's *really* needed.



Ruby
----

+ 2 spaces for tabs


Rails
-----

+ Devise for authentication

+ rspec for tests

+ factory_girl for factories

+ haml for views

+ jQuery for JS

+ Try real hard to stick to RESTful controllers. Think hard before adding a method to a controller that isn't one of the 7: index, new, create, show, edit, update, destroy.

+ Don't use scaffolding

+ Consider using [resource\_this](https://github.com/jnewland/resource_this) for your fairly straight forward resource'y controllers.

