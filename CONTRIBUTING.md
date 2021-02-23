If you have a board you'd like to contribute, the preferred method for submission is to create a modified version of the overlay [template](https://github.com/Gadgetoid/Pinout.xyz/blob/master/draft/overlay/template.md) and create a pull request. Please ensure the files you submit are being pushed to the `/draft` folder, where it will be reviewed before publication.

Note that as part of the submission, a top-down view of the board in the form of a [png](https://github.com/Gadgetoid/Pinout.xyz/blob/master/draft/boards/template.png) is expected. If you can't produce the png file yourself, just duplicate and rename `template.png` but make sure to include a url somewhere in the overlay where we can fetch a suitable graphic.

Once your draft has been made, before filing a pull request, you should try to render the page and make sure it build and appears as intended. To do so:

```
./draft/publish.sh myboard
make serve LANG=en
```
And then open: [http://127.0.0.1:5000](http://127.0.0.1:5000/) in your browser.

Once you are happy with the result,
```
./draft/unpublish.sh myboard
```
(this will file the overlay back into the draft folder, ready for review)

*note 1: you will need several python modules installed on your system to render and serve a local version of the site, run
`*pip install -r requirements.txt*` from the top of the repository tree to install the required modules.*

*note 2: if you are facing issues with your preview (board not showing, text update not appearing, etc.), you can fix it by erasing your browser's cache (image and cache file only).*

If you feel that the requirements for submissions is beyond your current possibilities, you may raise an [issue](https://github.com/Gadgetoid/Pinout.xyz/issues) requesting the addition of a specific board instead and we'll consider it!

## Running in Docker

The webserver can also be run in a Docker container. To do this, you first need to build the Docker image:
```
docker build -t pinout.xyz .
```
Next, you can start the containerized webserver:
```
docker run -p 5000:5000 -e PINOUT_LANG=en pinout.xyz
```
Now you can access the webserver at [http://127.0.0.1:5000](http://127.0.0.1:5000/).

# Translating

If you would like to provide support for a language not yet in the repository you should start by duplicating the `src/en` directory to the appropriate [language-code](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes). For example, if you want to create a Czech translation you would create the folder `src/cs`. Note that there are no plans to support cultures (it would just get out of hand), so you can't have `src/fr-CA` (sorry!).

The first resources we recommend you translate are the language-specific strings found in the `settings.yaml` file, `pi-pinout.md`, `index.md`, `404.md` and the `footer.html` template, as well as the content of the `/pin` folder, preferably.

Once that's done, rename the `/overlay` folder to `/translate` and start translating the boards markdown files (pick any you fancy translating, it does not have to be the first board in alphabetical order). Leave those translations in the `/translate` folder when finished.

Please do not attempt to translate the `/resources` folder, or anything not specifically mentioned in this section of the README - all files outside your <*languagecode*> directory are shared between the subdomains and are meant to be generic. Feel free to modify the template with links relevant to your country, and / or your Twitter handle however, but don't fiddle with the structure!

Once you've made your translation, you can build and preview it with, for example:
```
make serve LANG=de
```
And then open: [http://127.0.0.1:5000](http://127.0.0.1:5000/) in your browser.

The last step will be to submit your finished translation as a [pull request](https://github.com/Gadgetoid/Pinout.xyz/pulls) (this can include any number of boards, it does not have to be the entire line-up) and we'll get it live on its own <*languagecode*>.pinout.xyz subdomain.

If you wish to provide a translation for an existing subdomain, or correct a typo in an existing markdown file, just edit the file in place (leaving the files in the `translate` folder for review, if you are pushing a translation).

If you have a question about translations, raise an [issue](https://github.com/Gadgetoid/Pinout.xyz/issues) and we'll be happy to help you get past whatever hurdle you may face!

# Roadmap & wishlist
- Redesign HTML generation and unify HTML templates into a single, translatable file
- Add functionality to compare two or more boards, to visualise pin compatibility
- Tool to convert WiringPi to GPIO to BCM and back
- Add as many [boards](http://pinout.xyz/boards) as possible!
