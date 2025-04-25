NodeJS Multiple Application Hosting
===================================

### Referecne to workflow
### https://github-actions-hero.now.sh/
### https://github-actions-hero.vercel.app/

### About
This is sample project to demostrate multiple application hosting in node.js with Express.

### Structure

    |
    +-- app.js (<-- main. sometimes named "server.js")
    |
    +-- root
          |
          +-- Web1
          |     +-- img
          |     |    +-- Web1.jpg
          |     +-- index.js
          +-- Web2
          |     +--- img
          |     |     +-- Web2.jpg
          |     +--- index.js
          +-- manager.js

"Web1" and "Web2" represent independent app(context).
In each "index.js", you can code in the same way in "app.js", like this:

    app.get([path to this context], function(req,res){
        //do something
    })

###

- in app.js

        require("./root/manager.js").init(app, express);

- in "index.js" of each context(ex. "Web1","Web2")

        var app = require("../manager.js").getApp(__dirname);
