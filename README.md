# Quiz example code
This is a example for a simple quiz 
## How to run
1. Clone the repository
2. Run `npm install`
3. Run `npm start`
4. Open your browser and go to `http://localhost:3000`
## How to edit questions
1. go to `src/index.html`
2. In the `questions` element, follow the following structure and fill in between the brackets:
```html
<div id="question_(question number)_div">
    <h4 id="q3">(question)</h4>
    <input type="text" name="question (question number)" id="question_(question number)" data-answer="(answer of the question)">
</div><br><br>
```
3. In the script tag, follow the following structure and fill in between the brackets:
```js
async function question(question_number)_submit() {
        var question_(question_number) = document.getElementById("question_(question_number)");
        question_(question_number).disabled = true;
        //set the cookie 1 to the value of the question and remove the expiry date
        document.cookie = "question_1=" + question_(question_number).value + "; expires=Thu, 01 Jan 3000 00:00:00 UTC; path=/;";
        //check if the answer is correct
        if (question_(question_number).value === question_(question_number).dataset.answer) {
            question_(question_number).style.backgroundColor = "green";
            question_(question_number).style.color = "white";
            return true;
        } else {
            question_(question_number).style.backgroundColor = "red";
            question_(question_number).style.color = "white";
            return false;
        }
}
```	
4. Add the newly made functions to the submit_all function at the start
5. In the html, edit the number in the score element to the amount of questions you have
6. In the script tag and in the submit_all() function, edit the score_total variable to the amount of questions you have
## How to contribute
1. Fork the repository
2. Make your changes
3. Make a pull request
## How to build the project
1. Run `npm run build`
2. The build will be in the `dist` folder
## Credits
Here are all the packages used in this project:
- [Vite](https://vitejs.dev/)

And here are all the people who contributed to this project:
- nobody yet
## Distribution
You can freely distribute this project, but please give credit to the original author and do not claim it is yours.
## License
This project is licensed under the creative commons license. You can find the license [here](https://creativecommons.org/licenses/by-nc-sa/4.0/).
