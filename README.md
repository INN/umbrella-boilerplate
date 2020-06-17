# Getting started:

1. [Click this link](./issues/new?title=Setup+tasks&body=Setup tasks for creating the boilerplate repo%3A%0A%0A- [ ] run `.%2Finitialize.sh`%0A- [ ] set team permissions%0A- [ ] remove setup instructions from `README.md`%0A- [ ] update `README.md` for this site) to generate the first issue in this repo.
2. Complete that issue.

# Copy This Site Locally

This repository is designed to be set up in accordance with either the VVV or the Laravel Valet instructions in INN/docs. The current version of those docs can be found at https://github.com/INN/docs/blob/master/projects/largo/umbrella-setup.md

Things you need for this site:

- site URL: `TKTKNAME`
- project name: `TKTKNAME`
- site theme/plugin textdomain: `TKTKNAME`
- Constant name for constant variable purposes: `TKTKNAME`

# Creating a new site umbrella repository using this repository

This is referenced in the instructions for creating a new site and umbrella repository at https://github.com/INN/docs/blob/master/projects/largo/umbrella-setup.md and covers the creation of the new umbrella repository.

Using `sitename.org` as an example, and providing full pathnames in front of command-line prompts to help keep you located:

1. Pick a slug for this project. `sitename.org` might become `sitename`.
2. Generate a new repository for this site from INN's umbrella boilerplate by clicking this link: https://github.com/INN/umbrella-boilerplate/generate
	- INN projects should be generated in the INN organization, as `umbrella-sitename`
3. Clone the newly-generated repo to your local machine, in whatever way works with your local server setup, and do setup tasks.
6. Now, initialize the submodules and do some other things.
	
	In vvv:

	```
	/vagrant-local/www/sitename$ git clone git@github.com:INN/umbrella-sitename.git htdocs
	/vagrant-local/www/sitename$ cd htdocs
	/vagrant-local/www/sitename/htdocs$ ./initialize.sh
	/vagrant-local/www/sitename/htdocs$ git status
	On branch production
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

		new file:   .git-ftp-ignore
		new file:   .gitignore
		new file:   .gitmodules
		new file:   README.md
		new file:   wp-content/themes/largo

	```
	In Valet:
	
	```
	~/sites$ git clone git@github.com:INN/umbrella-boilerplate.git sitename
	~/sites/sitename$ ./initialize.sh
	~/sites/sitename$ git status
	On branch production
	Changes to be committed:
	  (use "git reset HEAD <file>..." to unstage)

		new file:   .git-ftp-ignore
		new file:   .gitignore
		new file:   .gitmodules
		new file:   README.md
		new file:   wp-content/themes/largo

	```
	
	Note that that will remove the `initialize.sh` script and this README file.

7. Copy in the child theme, if one exists.
	1. Make sure that the child theme's `style.css` entry for `Template:` matches the theme directory that we've cloned Largo in, `largo`. If they differ, `git mv` the Largo directory to match the `Template:` value.
	5. `cd ../../` : go back to the root of the project

8. Edit files to reflect the appropriate variables for this installation:
	- `README.md` - perform find-and-replace with domain name, but also check the instructions from the `vv create` setup
	- `.gitignore` - see comment at bottom of file; you need to add the child theme's directory name here

9. Prepare to commit: use `git add` to add the child theme and any other files.
	- Note that the child theme is not a submodule in this setup - we are incorporating the files directly into the theme. If you don't see individual files within the child theme from the umbrella repository when you're running `git add`, something has gone wrong.

10. Commit: `git commit`

This doesn't set any variables. This doesn't fill out any text. This just gets you the files.

Next steps for you:
- update README.md
