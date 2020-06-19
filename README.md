# Getting started:

<!-- remove this section after the repo is set up -->

1. [Click this link](./issues/new?title=Setup+tasks&body=Setup%20tasks%20for%20creating%20the%20boilerplate%20repo%3A%0A%0A-%20%5B%20%5D%20run%20%60.%2Finitialize.sh%60%0A-%20%5B%20%5D%20set%20team%20permissions%0A-%20%5B%20%5D%20remove%20setup%20instructions%20from%20%60README.md%60%0A-%20%5B%20%5D%20update%20%60README.md%60%20for%20this%20site%20to%20generate%20the%20first%20issue%20in%20this%20repo.%20%28Only%20works%20if%20you%27re%20clicking%20it%20from%20the%20root%20of%20the%20newly-created%20repo%20on%20GitHub%29) to generate the first issue in this repo. (Only works if you're clicking it from the root of the newly-created repo on GitHub)
2. Complete that issue.

# Copy TKTK Site Locally

This repository is designed to be set up in accordance with either the VVV or the Laravel Valet instructions in INN/docs. The current version of those docs can be found at https://github.com/INN/docs/blob/master/projects/largo/umbrella-setup.md

Things you need for this site:

- site URL: `TKTKNAME`
- project name: `TKTKNAME`
- site theme/plugin textdomain: `TKTKNAME`
- Constant name for constant variable purposes: `TKTKNAME`

# Creating a new site umbrella repository using this repository

<!-- feel free to delete this section once you've created this repo -->

This is referenced in the instructions for creating a new site and umbrella repository at https://github.com/INN/docs/blob/master/projects/largo/umbrella-setup.md and covers the creation of the new umbrella repository.

Using `sitename.org` as an example, and providing full pathnames in front of command-line prompts to help keep you located:

1. Pick a slug for this project. `sitename.org` might become `sitename`.
2. Generate a new repository for this site from INN's umbrella boilerplate by clicking this link: https://github.com/INN/umbrella-boilerplate/generate
	- INN projects should be generated in the INN organization, as `umbrella-sitename`
3. Clone the newly-generated repo to your local machine, in whatever way works with your local server setup, and do setup tasks.
4. Now, initialize the submodules and do some other things.
	
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

5. Copy in the child theme, if one exists.
	1. Make sure that the child theme's `style.css` entry for `Template:` matches the theme directory that we've cloned Largo in, `largo`. If they differ, `git mv` the Largo directory to match the `Template:` value.
6. Edit files to reflect the appropriate variables for this installation:
	- `README.md` - update `TKTK` strings with appropriate values.
	- `.gitignore` - see comment at bottom of file; you need to add the child theme's directory name here
7. `git grep TK` to find instances of placeholders in the boilerplate that need to be updated, and update them.
8. Prepare to commit: use `git add` to add the child theme and any other files.
	- Note that the child theme is not a submodule in this setup - we are incorporating the files directly into the theme. If you don't see individual files within the child theme from the umbrella repository when you're running `git add`, something has gone wrong.
9. Commit changes and push to the new repo.
