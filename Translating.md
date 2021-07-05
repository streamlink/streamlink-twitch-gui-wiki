Translating Streamlink Twitch GUI
====

1. [Introduction](#1-introduction)
2. [Technical details](#2-technical-details)
    1. [EditorConfig](#21-editorconfig)
    2. [Language codes](#22-language-codes)
    3. [Format](#23-format)
    4. [Structure](#24-structure)
    5. [Variables](#25-variables)
    6. [Missing translations](#26-missing-translations)
    7. [Hotkeys](#27-hotkeys)
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

The minimal requirements for writing and contributing translations is having a little bit of knowledge of Git, how to use it and how to submit pull requests on the project's GitHub repository. If you don't know how version control with Git works, please take a look at the online ["Pro Git" book](https://git-scm.com/book/en/v2) or the [help section on GitHub](https://help.github.com/) and get yourself comfortable with it. The project's [contributing guide](https://github.com/streamlink/streamlink-twitch-gui/blob/master/CONTRIBUTING.md#pull-requests) also explains how to fork, clone and branch, and how to create pull requests. If you're having trouble or any questions, don't hesitate to ask on the project's [Gitter.im channel](https://gitter.im/streamlink/streamlink-twitch-gui) or [GitHub issue tracker](https://github.com/streamlink/streamlink-twitch-gui/issues).

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

All currently included languages can be found in the `src/config/locales.json` file, which is used for dynamically importing all translations and language specific configurations. The translation files themselves are located in the `src/app/locales/` directory.

Each locale subfolder consists of multiple `.yml` files which all represent a logical translation namespace, based on the application structure and where their translations are included and loaded from. All YAML files contain a set of nested translation path names. These paths, in combination with their namespace (file name), are used for defining a specific translation string, eg. `settings.menu.header`, which the application uses to translate the "Settings" menu title.

### 2.5 Variables

Translation strings sometimes include `{variables}` which are replaced with dynamic values provided by the application code. There are different variable types with special syntax ([ICU message syntax](https://formatjs.io/docs/core-concepts/icu-syntax)) and formats, depending on the type.

When using a special variable type, the syntax is `{variable, type, format-or-parameters}`.

#### Simple text substitution

```yaml
# en/messages.yml
welcome: "Welcome, {user}"
```

```yml
# de/messages.yml
welcome: "Willkommen, {user}"
```

```js
intl.locale = [ "en" ];
intl.t( "messages.welcome", { user: "Anonymous" } ) === "Welcome, Anonymous";

intl.locale = [ "de" ];
intl.t( "messages.welcome", { user: "Anonymous" } ) === "Willkommen, Anonymous";
```

#### Number formats

Number formats vary between different languages. Variables of the type `number` will be formatted automatically, with optional parameters depending on the kind of number that's being translated.

See [the `number` type explanation of FormatJS](https://formatjs.io/docs/core-concepts/icu-syntax#number-type) for more information.

#### Date or time formats

Similar to numbers, dates and times are described differently in different languages. Variables of the types `date` and `time` always have a special format name defined, eg. `full` or `short`, which is then used to find the most fitting format depending on the language. The same format name should be kept when translating, as it will carry the same information when being translated.

See [the `date` and `time` type explanations of FormatJS](https://formatjs.io/docs/core-concepts/icu-syntax#date-type) for more information.

```yml
# en/channel.yml
created: {created_at, date, full}
online: {since, time, medium}
```

```yml
# de/channel.yml
created: {created_at, date, full}
online: {since, time, medium}
```

```js
intl.locale = [ "en" ];
intl.t( "channel.created", { created_at: new Date() } ) === "Sunday, July 4, 2021";
intl.t( "channel.online", { online: new Date() } ) === "01:33:37 PM";

intl.locale = [ "de" ];
intl.t( "channel.created", { created_at: new Date() } ) === "Sonntag, 4. Juli 2021";
intl.t( "channel.online", { online: new Date() } ) === "13:33:37";
```

#### Pluralization

Languages can have different pluralization rules. This makes it difficult when translations rely on variables with values of a certain quantity.

Variables which require pluralization are of the type `plural` and have a set of certain formats defined, depending on the language and the variable's potential values:

- `one`
- `two`
- `few`
- `many`
- `other` (required - general plural form)
- `=value` (special translations required by the app logic)

Which parameters are going to be used depends on the language's pluralization rules, so not all parameters need to be defined for each locale. For example, English and many other European languages only use `one` and `other`. Fixed values are defined by the application's logic and always need to be included if they exist.

See [the `plural` type explanation of FormatJS](https://formatjs.io/docs/core-concepts/icu-syntax#plural-format) or the [plural rules](https://unicode.org/cldr/charts/latest/supplemental/language_plural_rules.html) of the Unicode Common Locale Data Repository for more information.

```yml
# en/users.yml
online: |
    There {count, plural,
        =0 {are no users}
        one {is one user}
        other {are # users}
    } online right now!
```

```yml
# de/users.yml
online: |
    Zur Zeit {count, plural,
        =0 {ist kein Nutzer}
        one {ist ein Nutzer}
        other {sind # Nutzer}
    } online!
```

```js
intl.locale = [ "en" ];
intl.t( "users.online", { count: 0 } ) === "There are no users online right now!";
intl.t( "users.online", { count: 1 } ) === "There is one user online right now!";
intl.t( "users.online", { count: 1000 } ) === "There are 1,000 users online right now!";

intl.locale = [ "de" ];
intl.t( "users.online", { count: 0 } ) === "Zur Zeit sind keine Nutzer online!";
intl.t( "users.online", { count: 1 } ) === "Zur Zeit ist ein Nutzer online!";
intl.t( "users.online", { count: 1000 } ) === "Zur Zeit sind 1.000 Nutzer online!";
```

### 2.6 Missing translations

If a translation is missing and can't be found, `ember-intl` will try to use a fallback locale for looking it up. For locales with a region subtag, their parent locale will be looked up first, otherwise, `en` will be used as a global fallback. Missing translations in the `en` locale (which is the developer's fault) result in a `Missing translation: {path}` message being shown.

### 2.7 Hotkeys

Another special part of each locale are hotkey translations, which are shown in tooltips or in the hotkeys settings menu. Hotkeys consist of optional modifier keys, like `ctrlKey`, `shiftKey`, `altKey` or `metaKey`, and special key codes, like for example `KeyA` or `ArrowLeft`, which may need to be translated or shortened in order to sound more natural.

These codes are defined by the DOM Level 3 Events Specification and describe the [`code`](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code) property of a [`KeyboardEvent`](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent) object. This `code` property differs from the KeyboardEvent's usually used `key` property in the sense that it represents a physical key on the user's keyboard as opposed to the character the keypress would otherwise generate. In more simple words, this property returns a value which isn't altered by the keyboard layout or the state of the modifier keys.

Since these codes are simple words or combinations of words of the English language, the `en` locale doesn't include "translations" for each code. This translation list of codes however is dynamic and codes can optionally be added by the translator. [Codes of alphanumeric keys](https://www.w3.org/TR/uievents-code/#key-alphanumeric-writing-system) already get mapped to logical key names via Chromium's available `KeyboardLayoutMap`s and therefore don't need to be translated or renamed:

```text
 KeyA   -> A   ...   KeyZ   -> Z
 Digit0 -> 0   ...   Digit9 -> 9
```

As a final example, hotkey translations in the German `de` locale could look like this:

```text
codes:
    Insert: Einfügen
    Delete: Entfernen
    Space: Leertaste
    ...
```

See a list of all available KeyboardEvent codes in the MDN web docs:  
https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/code/code_values

Further technical details can be found in the official W3C documentation:

- https://www.w3.org/TR/DOM-Level-3-Events/#interface-keyboardevent
- https://www.w3.org/TR/DOM-Level-3-Events/#keys-codevalues
- https://www.w3.org/TR/uievents-code/

Or on the KeyboardMap API docs of the Web Platform Incubator Community Group:

- https://wicg.github.io/keyboard-map/#introduction


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

#### Language icon

Since the language selection dropdown in the settings menu also includes flags for representing a language (which is not an ideal but good enough solution), flag icons based on the language code need to be loaded. See whether `src/config/langs.json`, the file responsible for mapping language codes to flag icons, already includes the language code. If it does not, add a new object to it (mind the sort order) and choose a flag value which can be loaded from the [`flag-icon-css`](https://yarnpkg.com/en/package/flag-icon-css) library in its currently included version (see `package.json`). Don't forget to set the `disabled` property to `true`. This will exclude the language from the stream filtering mechanic as the set of supported languages is defined by Twitch and not by Streamlink Twitch GUI.

### 3.3 Testing

In order to see if everything is working properly, you need to build the application. First, close already running instances of Streamlink Twitch GUI, as it doesn't allow running multiple instances of it at the same time.

If you haven't installed the project's dependencies yet, you have to do it now. The [contributing guide](https://github.com/streamlink/streamlink-twitch-gui/blob/master/CONTRIBUTING.md#developing-and-building) has more detailed informations.

```bash
# install the project's build- and runtime dependencies
yarn install
```

Get a list of missing, invalid or unused translation strings first:

```bash
yarn run grunt webpack:i18n
```

Then run a development build:

```bash
yarn run grunt build
```

This command builds and then launches the application in development mode and will also automatically rebuild it as soon as any file being included or folder being watched gets changed. See the log output for the current build status and reload the application window to see your changes (click the reload button at the top or press `CTRL+R` in the dev tools window, if opened - hot module reloading is not available). Press `CTRL+C` in the terminal window to exit the application and stop rebuilding it.

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
