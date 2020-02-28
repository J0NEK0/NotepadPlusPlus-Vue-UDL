# UDL for .vue files in Notepad++
This project provides a quick and simple way to enhance the development of Vue single-file components with Notepad++.
As I'm writing, I'm not aware of any plugin realising the single-file component syntax highlighting or .vue support coming anytime soon for Notepad++.
The best way so far seems to be using Javascript-highlighting but I became dissatisfied of it quite fast, especially when writing the template-part.
So I decided to define a new highlighting using the User-Defined-Language tool of Notepad++.  
There's another project from [meatballcoder](https://github.com/meatballcoder/notepadplusplus-vue-syntax-highlighting) also defining a UDL for .vue files but unfortunately it appears to be broken.
Thus I created another UDL realising Vue single-file component highlighting in an acceptable manner based on the themes Notepad++ uses for Javascript and HTML.

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
