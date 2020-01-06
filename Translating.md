Translating Streamlink Twitch GUI
====

1. [Introduction](#1-introduction)
2. [Technical details](#2-technical-details)
    1. [EditorConfig](#21-editorconfig)
    2. [Language codes](#22-language-codes)
    3. [Format](#23-format)
    4. [Structure](#24-structure)
    5. [Variables](#25-variables)
    6. [Pluralization](#26-pluralization)
    7. [Missing translations](#27-missing-translation)
    8. [Hotkeys](#28-hotkeys)
3. [Translating](#3-translating)
    1. [Setup](#31-setup)
    2. [Adding new translations](#32-adding-new-translations)
    3. [Testing](#33-testing)
    4. [Committing changes](#34-committing-changes)
    5. [Submitting changes](#35-submitting-changes)
4. [Style guidelines](#4-style-guidelines)
   1. [Accuracy & Context](#41-accuracy--context)
   2. [Punctuation](#42-punctuation)
   3. [Length](#43-length)

----

## 1. Introduction

This guide describes how to help translating Streamlink Twitch GUI. If you're interested in improving or adding new translations, even if you don't have any programming experience, please continue reading, as this guide will try to cover all of the basics, as well as the setup and workflow.

The minimal requirements for writing and contributing translations is having a little bit of knowledge of Git, how to use it and how to submit pull requests on the project's GitHub repository. If you don't know how version control with Git works, please take a look at the online ["Pro Git" book](https://git-scm.com/book/en/v2) or the [help section on GitHub](https://help.github.com/) and get yourself comfortable with it. The project's [contributing guide](https://github.com/streamlink/streamlink-twitch-gui/blob/master/CONTRIBUTING.md#pull-requests) also explains how to fork, clone and branch and how to create pull requests. If you're having trouble or any questions, don't hesitate to ask on the project's [Gitter.im channel](https://gitter.im/streamlink/streamlink-twitch-gui) or [GitHub issue tracker](https://github.com/streamlink/streamlink-twitch-gui/issues).

Your help is very much appreciated, thank you!


## 2. Technical details

### 2.1 EditorConfig

Streamlink Twitch GUI uses an [EditorConfig](http://editorconfig.org/). This config tells the text editor to behave in a certain way, according to the defined rules, like writing files with UTF-8 encoding without BOM, using UNIX style line endings, including a new line at end of the document and setting the whitespace indentation style and size. If your text editor does not have built-in EditorConfig support, please follow these simple rules manually on your own.

### 2.2 Language codes

When working with multiple languages in software development, languages need unique identification codes in order to be able to process their data. These codes are standardized by the [IETF BCP 47](https://tools.ietf.org/html/bcp47).

Before you're going to add translations for a not yet included language, please pick the right code for it. For compatibility reasons, all codes need to be lowercased and dashes need to be used instead of underscores.

The [Unicode language identifier specification](https://www.unicode.org/reports/tr35/tr35-49/tr35.html#Unicode_language_identifier) and [W3C language tags documentation](https://www.w3.org/International/articles/language-tags/index.en) are a good source of further information. [Useful helper tools](https://r12a.github.io/app-subtags/) for finding and validating these language codes also exist.

#### Examples

| Code | Language |
| :-- | :-- |
| `en` | English |
| `en-gb` | British English |
| `en-us` | American English |
| `de` | German |
| `de-ch` | Swiss-German |
| `pt` | Portuguese |
| `pt-br` | Brazilian |

### 2.3 Format

Translations are written in the simple, human-readable [YAML format](https://en.wikipedia.org/wiki/YAML). If you don't know YAML, please read [this](https://learnxinyminutes.com/docs/yaml/) short document, which will teach you the basics.

#### Indentation

The indentation size of all YAML files is 4 spaces.

#### Strings

There are a couple of different ways of defining strings in YAML. Quotation marks can often times be omitted, but only if it doesn't conflict with other syntax rules. This can sometimes be an issue when translations include variables, special characters or whitespace at certain positions. The rule here is to omit quotation marks where possible for having a cleaner look and use double quotes only where it is required. In certain cases, quotation marks may also be added to sibling translations for having a more consistent style.

#### Comments

Comments should be added above translations or entire blocks of translations which require further improvements, eg.

```yaml
# FIXME: incomplete translation
```

Already existing comments from the English template should always be kept, as these are used for important annotations.

### 2.4 Structure

All currently included languages can be found in the `src/config/locales.json` file, which is used for dynamically importing all translations and language specific configurations. The translation and config files themselves are located in the `src/app/locales/` directory.

Each locale subfolder consists of a `config.js` file and multiple `.yml` files, which all represent a logical translation namespace, based on the application structure and where their translations are being included and loaded from. All YAML files contain a set of nested paths (trees/objects) of translation path names. These paths, in combination with their namespace, are used for defining a specific translation string, eg. `settings.menu.header`, which translates to "Settings" in the `en` locale. The locale's `config.js` file is used for defining the language configuration, like pluralization rules for example.

### 2.5 Variables

There are two different kinds of variable translation strings: ones which include regular `{{variables}}` and special ones, which are used for formatting MomentJS strings, like times and dates.

#### Regular variables

Regular variables are simple text substitutions and have logical names based on the English text template. This should make it clear when a variable is representing a number, version string, or when it is based on user data, like a name of a channel for example. Using those variables in a translation should be fairly simple. Some other variables are a bit more complex though, and are based on other translations, which can potentially make it a bit more difficult. These kinds of variables are mostly just simple words, like localized language names, but can also be the output of localized MomentJS strings, like "a day" or "3 months". Please make sure that all possible values of all variables fit into the translated texts. If a variable is based on MomentJS output, it is annotated and the [documentation](https://momentjs.com/docs/#/displaying/) of the respective method call should be read. The localization config of MomentJS can be found [here](https://github.com/moment/moment/tree/master/src/locale).

#### MomentJS formats

The second type of variable translations are formattable MomentJS strings (which are always annotated). These strings work differently, as they are used as the parameter for MomentJS' `format` method instead. Please see the MomentJS [format documentation](https://momentjs.com/docs/#/displaying/format/) for a list of all available variables and how to escape regular text.  
 To ensure that a specific translation string is using consistent formats across all languages (eg. short or long time and date formats), localized format variables like `LTS` or `LLLL` should be used. If those don't fit grammar-wise, custom formats can of course be defined, as long as they are similar to the intended localized formats.

#### Examples

```yaml
# en-gb/messages.yml
welcome: "Welcome, {{user}}"
remaining: "Only {{time}} left"
today: "dddd, [the] Do [of] MMMM"

# de/messages.yml
welcome: "Willkommen, {{user}}"
remaining: "Nur noch {{time}} übrig"
today: "dddd, [der] DD. MMMM"
```

```js
const time = new Moment().to( twoMonths, true );

// en-gb
i18n.t( "messages.welcome", { user: "foo" } ) === "Welcome, foo";
i18n.t( "messages.remaining", { time } ) === "Only 2 months left";
new Moment().format( i18n.t( "messages.today" ) ) === "Monday, the 12th of March";

// de
i18n.t( "messages.welcome", { user: "foo" } ) === "Willkommen, foo";
i18n.t( "messages.remaining", { time } ) === "Nur noch 2 Monate übrig";
new Moment().format( i18n.t( "messages.today" ) ) === "Montag, der 12. März";
```

### 2.6 Pluralization

Languages can have different pluralization rules. This makes it difficult when translations rely on variables with values of a certain quantity.

Those pluralization rules are configured by the `config.js` file of each locale and are usually imported from the i18n library being used (`ember-i18n`), but can also be customized, if needed.

Translation strings which require pluralization are indicated by the usage of the special `{{count}}` variable and a subset of these special properties:

- `zero` (*)
- `one`
- `two`
- `few`
- `many`
- `other` (required - general plural form)

Which properties are going to be used depends on the locale's pluralization rules, so not all properties need to be defined for each locale. For example, English and many other European languages only use `one` and `other`.

(*) In some special cases, pluralized translations may statically reference their `zero` property, even if a locale doesn't define `zero` in its pluralization rules. This depends on how the translation string has been implemented, eg. when a zero value needs a different text. This is annotated with a comment.

See `ember-i18n`'s [pluralization wiki page](https://github.com/jamesarosen/ember-i18n/wiki/Doc:-Pluralization) or the [plural rules](https://unicode.org/cldr/charts/latest/supplemental/language_plural_rules.html) of the Unicode Common Locale Data Repository for more information.

#### Examples

```yaml
# en/fruits.yml
#   English has the following pluralization rules:
#   one: n==1
#   other: n!=1
apples:
    one: "One apple"
    other: "{{count}} apples"

# fr/fruits.yml
#   French has the following pluralization rules:
#   one: n>=0 and n<2
#   other: n<0 or n>=2
apples:
    one: "{{count}} pomme"
    other: "{{count}} pommes"
```

```js
// en
i18n.t( "fruits.apples", { count: 0 } ) === "0 apples";
i18n.t( "fruits.apples", { count: 1 } ) === "One apple";
i18n.t( "fruits.apples", { count: 2 } ) === "2 apples";

// fr
i18n.t( "fruits.apples", { count: 0 } ) === "0 pomme";
i18n.t( "fruits.apples", { count: 1 } ) === "1 pomme";
i18n.t( "fruits.apples", { count: 2 } ) === "2 pommes";
```

### 2.7 Missing translations

If a translation is missing and can't be found, `ember-i18n` will try to use a fallback locale for looking it up. For locales with a region subtag, their parent locale will be looked up first, otherwise, `en` will be used as a global fallback. Missing translations in the `en` locale (which is the developer's fault) result in a `Missing translation: {{path}}` message being shown.

### 2.8 Hotkeys

Another special part of each locale are hotkey translations, which are shown in tooltips or in the hotkeys settings menu. Hotkeys consist of optional modifier keys, like `controlKey`, `shiftKey`, `altKey` or `metaKey`, and special key codes, like for example `KeyA` or `ArrowLeft`, which may need to be translated or shortened in order to sound more natural.

These codes are defined by the DOM Level 3 Events Specification and describe the [`code`](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code) property of a [`KeyboardEvent`](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent) object. This `code` property differs from the KeyboardEvent's usually used `key` property in the sense that it represents a physical key on the user's keyboard as opposed to the character the keypress would otherwise generate. In more simple words, this property returns a value which isn't altered by the keyboard layout or the state of the modifier keys.

Since these codes are simple words or combinations of words of the English language, the `en` locale doesn't include "translations" for each code. This list of codes however is dynamic and codes for all possible keys can be added by the translator.

Certain codes already get shortened by the application's `HotkeyService` itself, like for example:

```text
 KeyA   -> A  ...  KeyZ   -> Z
 Digit0 -> 0  ...  Digit9 -> 9
```

See a list of all available KeyboardEvent codes in the MDN web docs:  
https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code/code_values

Further technical details can be found in the official W3C documentation:

- https://www.w3.org/TR/DOM-Level-3-Events/#interface-keyboardevent
- https://www.w3.org/TR/DOM-Level-3-Events/#keys-codevalues
- https://www.w3.org/TR/uievents-code/


## 3. Translating

In addition to this section, please see the project's [contributing guide](https://github.com/streamlink/streamlink-twitch-gui/blob/master/CONTRIBUTING.md#developing-and-building), which includes further information on how to build the application and how to fork and submit pull requests. And before you start, make sure that all required developing tools (Git, NodeJS and Yarn/Npm) are correctly installed.

### 3.1 Setup

First, fork Streamlink Twitch GUI on GitHub. This will copy the entire repository onto your GitHub account. Then locally clone your fork from GitHub and register the upstream repository:

```bash
# clone your forked repository
git clone "git@github.com:USERNAME/streamlink-twitch-gui.git"
cd streamlink-twitch-gui
# add the remote repository and call it "upstream"
git remote add upstream "https://github.com/streamlink/streamlink-twitch-gui.git"
# you should now have an "origin" and an "upstream" remote repository
git remote -v
```

Now branch off the master branch. If you've cloned a while ago, get the latest changes first:

```bash
# checkout the master branch
git checkout master
# see whether your working tree is clean
git status

# pull the latest changes from the upstream master branch
git pull upstream master
```

If the master branch is up to date, branch off and give your new branch a proper name:

```bash
git checkout -b "i18n/LANGUAGECODE"
```

### 3.2 Adding new translations

#### Registering a new language

In order to register a new language, open the `src/config/locales.json` JSON file and add a new entry to the `locales` object. Use the correct language code as key and as value, use the localized language name (eg. `Deutsch` for German). The list should be kept sorted in alphabetical order by language code (keys).

#### Contributors list

You can optionally add yourself to the translation contributor list. Just copy the existing format if you're adding a new language (please adhere to the sort order of the `locales` object above), otherwise add yourself to the bottom of the existing locale's contributor list. The `github` field may be omitted if you don't want your GitHub account to be linked in the "About" menu later on.

#### Locale directory

Once the new language has been registered, create a new locale directory in `src/app/locales` and copy the contents of the `en` directory:

```bash
cp -r src/app/locales/en src/app/locales/LANGUAGECODE
```

#### Language configuration

Open `config.js` from the new locale folder and import the correct configuration file provided by `ember-i18n`. If `ember-i18n` doesn't provide a pre-defined configuration, import another one from `ember-i18n` that matches the desired config or define it yourself by using the available ones as a template.

#### MomentJS localizations

MomentJS localizations should be loaded automatically. If not, which is quite unlikely, add them to the `config.js` file by importing from `moment` and follow the localization guidelines of MomentJS. Already existing localization configs of MomentJS can also be found [here](https://github.com/moment/moment/tree/master/src/locale).

#### Language icon

Since the language selection dropdown in the settings menu also includes flags for representing a language (which is not an ideal but good enough solution), flag icons based on the language code need to be loaded. See whether `src/config/langs.json`, the file responsible for mapping language codes to flag icons, already includes the language code. If it does not, add a new object to it (mind the sort order) and choose a flag value which can be loaded from the [`flag-icon-css`](https://yarnpkg.com/en/package/flag-icon-css) library in its currently included version (see `package.json`). Don't forget to set the `disabled` property to `true`. This will exclude the language from the stream filtering mechanic as the set of supported languages is defined by Twitch and not by Streamlink Twitch GUI.

### 3.3 Testing

In order to see if everything is working properly, you need to build the application. First, close already running instances of Streamlink Twitch GUI, as it doesn't allow running multiple instances of it at the same time.

If you haven't installed the project's dependencies yet, you have to do it now. The [contributing guide](https://github.com/streamlink/streamlink-twitch-gui/blob/master/CONTRIBUTING.md#developing-and-building) has more detailed informations.

```bash
# install the grunt CLI tool globally (may require administrator privileges)
yarn global add grunt-cli
# install all of the project's build- and runtime dependencies
yarn install
```

Then run a development build:

```bash
grunt build
```

This command builds and then launches the application in development mode and will also automatically rebuild it as soon as any file being included or folder being watched gets changed. See the log output for the current build status and reload the application window to see your changes (click the reload button at the top or press `CTRL+r` in the dev tools window, if opened - hot module reloading is not available). Press `CTRL+c` in the terminal window to exit the application and stop rebuilding it.

### 3.4 Committing changes

Please commit your changes in logical chunks, eg. one commit for each locale namespace. Use `i18n/LANGUAGECODE: your message` as commit message format, which makes it easy to find all relevant commits in the future more quickly. If there is work left to do in the files being committed, optionally add a short TODO note in the commit message's body.

### 3.5 Submitting changes

Once you've finished your work (or if you want to share unfinished work), you can push the local branch to your forked repository on GitHub and submit a new pull request, so that your changes can be reviewed. Make sure that the branch doesn't include unnecessary or unrelated commits.

```bash
git push origin "i18n/LANGUAGECODE"
```

If you need to fix mistakes in any of the files, you can simply add more commits, or you can rebase the branch, which lets you edit previous commits. Make sure that the master branch is up to date, so that you also receive the latest updates.

```bash
# rebase and edit/reword/move/drop/squeeze your commits
git checkout "i18n/LANGUAGECODE"
git rebase --interactive master
# update the pull request
git push --force origin "i18n/LANGUAGECODE"
```


## 4. Style guidelines

Finding the right translations can often times be difficult. In some cases, and also depending on the language, translating words or entire phrases doesn't even make sense. Common translation rules need to be defined, in order to ensure a consistent style.

### 4.1 Accuracy & Context

Translations should always be as accurate as possible. This doesn't necessarily mean that the English text template has to be translated in a strict way. It is far more important to precisely describe the meaning of each line, based on the context, so that it sounds natural to another native speaker. Borrowing words from the English template (using anglicisms) is a legitimate thing to do if words or phrases can't be translated well enough.

### 4.2 Punctuation

Please notice the punctuation marks of the English template. If a line ends with a full stop, add one to your translation as well.

### 4.3 Length

Since you are translating a graphical user interface, it is important to keep an eye on the length of each translated string. The maximum supported length depends on the location where the string is being used and can more or less be dynamic, but if it exceeds its limit, it has to be rephrased and shortened. Please keep in mind that even if Streamlink Twitch GUI embeds all of its used fonts, text rendering will be different on each platform. If a translated string barely fits, it doesn't necessarily mean that it will also fit on another system.
