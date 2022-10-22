# Learn how to make a quiz like this

Hi! My name is Emile, I will be teaching you how to make your own quiz!

## Chapter 1: Getting started

In this chapter we will be setting up the project. You are going to need [Node.js](https://nodejs.org/en/) and [Git](https://git-scm.com/) installed on your computer. I also recommend installing [Visual Studio Code](https://code.visualstudio.com/) as your code editor and [vite](https://vitejs.dev/) globally as your development server.

### Step 1: set up your project

1. Open your terminal and navigate to the directory where you want the folder of the project to be created
2. run `npm init vite@latest` and follow the instructions
3. Select `vanilla` as the template
4. Now you can run `cd (project name)` to navigate to the project folder
5. Run `npm install` to install the dependencies (skip this step if you installed vite globally)
6. Run `npm run dev` to start the development server

### Step 2: set up your repository

1. Go to [GitHub](https://github.com) and create a new repository
2. Run `git init` to initialize git in your project
3. Run the following commands to connect your local repository to your remote repository:

```bash
git remote add origin
git branch -M main
git push -u origin main
```

4. Now you can run `git add .` to add all the files to the staging area and `git commit -m "Initial commit"` to commit the files to the repository
5. Run `git push` to push the files to the remote repository

## Chapter 2: Making the quiz

In this chapter, we will use vanilla JavaScript to make the quiz. We will be using the [Vite](https://vitejs.dev/) development server to run the project.

### Step 1: set up the HTML

1. Open the `index.html` file in your code editor
2. Replace the contents of the file with the following code:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Quiz</title>
</head>
<body>
    <h1>Quiz</h1>
    <question>
        <h4>( the question )</h4>
        <input type="text" placeholder="Your answer" data-answer="(the answer)">
    </question>
    <button onClick="submit_all()">Submit</button>
    <script type="module" src="/src/main.js"></script>
    <score>
        (ignore this)
    </score>
</body>
```
3. Save the file
4. Open the `src/main.js` file in your code editor
5. Replace the contents of the file with the following code:
```js
function submit_all() {
        //get all the questions
        var questions = document.getElementsByTagName("input");
        //remove the submit button from the list of questions
        questions = Array.from(questions).slice(0, -1);
        //get the score
        var score = document.getElementById("score");
        //set the score to 0
        score.innerHTML = "Score: 0/" + questions.length;
        //set the answers list to an empty list
        var answers = [];
        //for all the questions
        for (var i = 0; i < questions.length; i++) {
            //get the question
            var question = questions[i];
            question.disabled = true;
            //get the answer
            var answer = question.dataset.answer;
            //get the value of the question
            var value = question.value;
            //save the value to lower case
            var value = value;
            //save the answer to cookies
            document.cookie = "answer_" + i + "=" + value + ";SameSite=None;Secure";
            //if the given value is in the answer array
            if (answer.includes(value)) {
                //add 1 to the score
                score.innerHTML = "Score: " + (parseInt(score.innerHTML.split(":")[1].split("/")[0]) + 1) + "/" + questions.length;
                //make the question green
                question.style.backgroundColor = "green";
                question.style.color = "white";
                question.disabled = true;
            } else {
                //make the question red
                question.style.backgroundColor = "red";
                question.style.color = "white";
                question.disabled = true;
            }
            answers.push("Question " + i + ":" + value + '\n');
        }
        document.getElementById("submit").disabled = true;
        document.getElementById("submit").style.backgroundColor = "grey";
        document.getElementById("submit").style.color = "black";
        document.cookie = "Submit=true;SameSite=None;Secure";
    }
```
6. Save the file and go to `localhost:3000` in your browser to see the quiz
7. Edit in the `views/quiz.ejs` to the following code:
```js
//set in vitejs config the root to ./src
import { defineConfig } from 'vite'
export default defineConfig({
    root: './src',
    plugins: [],
    build: {
        outDir: '../dist',
        emptyOutDir: true
    }
});
```
8. You can now start making your quiz using the HTML from above normally.
## That's it!
You have now kind of made a quiz. It is not like the one in my respority, but my code is harder to explain. If you want to use mine go to [this repository](https://github.com/Emile2020/emiquiz) and follow the instructions in the README.md file. (DO NOT FORGET TO READ THE LICENSE)