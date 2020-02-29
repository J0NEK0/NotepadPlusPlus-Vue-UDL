# User Defined Language (UDL) for .vue files in Notepad++
This project provides a quick and simple way to enhance the development of Vue single-file components with Notepad++.
As I'm writing, I'm not aware of any plugin realising the single-file component syntax highlighting or .vue support coming anytime soon for Notepad++.
The best way so far seems to be using Javascript-highlighting but I became dissatisfied of it quite fast, especially when writing the template-part.
So I decided to define a new highlighting using the User-Defined-Language tool of Notepad++.  
There's another project from [meatballcoder](https://github.com/meatballcoder/notepadplusplus-vue-syntax-highlighting) also defining a UDL for .vue files but unfortunately it appears to be broken.
Thus I created another UDL realising Vue single-file component highlighting in an acceptable manner based on the themes Notepad++ uses for Javascript and HTML.
It also supports BootstrapVue.

## Installation
1. Copy the content of *Vue.xml* into a new file and save it as *Vue.xml* (or any other name if you want Notepad++ to display its name otherwise, e.g. *vue.xml* to start with a small letter)(git users may clone).
2. Open Notepad++ (if it isn't already).
3. Go to *Language -> User Defined Language -> Define your language*.
4. Click *Import*.
5. Select the XML-file you saved.
6. Close the dialog and restart Notepad++.
7. Go to *Language* again and select *Vue* (or however your named the file) right under *User Defined Language* to enable the highlighting for any .vue file in your current session. If you open any .vue files that aren't part of your current session, the language is automatically selected.

If you want to customize the highlighting you can do so by following *Language -> User Defined Language -> Define your language* and selecting *Vue* (or how you named the file you imported) in the dropdown menu.
Colors and font (sizes) are quite simple to change but you might want to read further below if you want to make major changes.

## How it's (not) working
A typical single-file component consists of three parts: *template*, *script* and *style*.
Basically all one has to do is to apply the consisting rules for *HTML*, *Javascript* and *CSS* to the correct part of the code and add the keywords for Vue.
However, the UDL of Notepad++ allows you only to create one language which is then applied to the whole content of a file.
This suggests that you'd have to merge all keywords from all languages together but then the *Javascript* keywords would also be highlighted in the *template* section.
To avoid this, I made use of the delimiters.
Nevertheless this approach still requires some language-mixing and waiver of some typical features.

### Delimiters
To apply specific rules to a specific part of the code I used delimiters and the nesting function.
Any code between `<template ... </template>` will have an HTML-like highlighting and also highlight Vue and BootstrapVue components.  
Code between `<script ... </script>` will be highlighted like Javascript for the most part and also highlight Vue keywords.  
The last part is the styling code between `<style ... </style>` and it will have a highlighting similar to CSS.

### Keywords
The UDL of Notepad++ allows to define eight sets of keywords and each set has it's own styling-options.
|Set|Usage|Description|
|---|:---:|-----------|
| 1 | template | BootstrapVue keywords, bold and lavender-colored |
| 2 | template | Vue directives and special attributes, bold and green |
| 3 | template | HTML keywords and attributes, bold and blue |
| 4 | script   | Vue keywords, bolad and green |
| 5 | script   | Javascript ternary keywords, bold and brown |
| 6 | script   | Javascript primary keywords mixed with secondary keywords, bold and blue |
| 7 | style    | CSS primary and secondary keywords, bold and lavender-colored |
| 8 | comment  | Javadoc keywords, bold and cyan |

### Comments & Numbers
The highlighting of numbers has to be globally declared.
Fortunately only Javascript has a highlighting for numbers, so the old style is copied and applied only to the *script* part.

Sadly the comments aren't that simple to handle.
While CSS and Javascript have at least the `/* */` in common, HTML does not.
Of course comments have to be declared globally and I decided to include all three types of comments (`//`, `/* */` and `<!-- -->`).
However this means that if you write a HTML-comment in the *script* part, it's highlighted as if it were correct but your code won't run.
As I can think of no fix for this given the UDL constraints, simply don't do it.

### Operators
Another tricky part are the operators.
The UDL distinguishes between two kind of operators.
The first kind can be glued to any variable or keyword, e.g. `i+=1`, and the other kind needs whitespace around it like `not true`.

Since there is a bad synergy between Javascript, HTML and CSS operators a couple of problems arises.
If I define `-` to be an operator of type 1 (needs no whitespace around), almost all Vue and BootstrapVue keywords won't be identified, since they contain a `-` and thus appear as two words.
To avoid this, I made `-` and `--` operators of type 2, meaning you have to write whitespaces around these two operators in order to make the highlighting work properly.

A similar problem occurs with the `<` and `>` operators.
They need to be defined as type 1 operator because otherwise the HTML, Vue and BootstrapVue keywords aren't recognized correctly since `<b-button != b-button`.
That is why this highlighting doesn't color the whole HTML tag as it would in pure HTML and can't distinguish CSS class- and id-selectors like pure CSS highlighting.

### Folding
A common functionality of editors is the ability to fold blocks of code at certain points, e.g. `{`and `}`.
In UDL this is another global characteristic and unfortunately it's not applicable to the delimiter-environments.
However, to not completely deny this feature, one can define such breakpoints in comments.
All you have to do is write `.fS` or `.foldStart` to mark the starting point and `.fE` or `.foldEnd` to mark the ending point.

![Comment-Folding](https://github.com/J0hann3s/NotepadPlusPlus-Vue-UDL/blob/master/img/folding.png)
