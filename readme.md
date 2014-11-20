rtCamp Docs
===========

This includes following details

- Product Documentation
- Release Notes
- Change Logs (Maybe)

Getting Started
====================

### Install Jekyll

	gem install jekyll

### Run Docs site on localhost

	git clone git@git.rtcamp.com:static/docs-rtcamp-com.git
	cd docs-rtcamp-com
	jekyll serve

### Create New Page

- Create pages easily via rake task:

	```
rake page name="about.md"
	```

- Create a nested page:

	```
rake page name="pages/about.md"
	```

- Create a page with a "pretty" path:

	```
rake page name="pages/about"
# this will create the file: ./pages/about/index.html
	```

### Publish

After you've added pages or made changes to your files, simply commit them to your git repo and push the commits up to server.

	git add .
	git commit -m "Addding new Doc"
	git push origin master

A git post-commit hook will automatically deploy your changes to http://docs.rtcamp.com.