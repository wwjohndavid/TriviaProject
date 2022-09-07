# react-quiz-component

:orange_book: React Quiz Component
[![NPM version](https://img.shields.io/npm/v/react-quiz-component.svg)](https://www.npmjs.com/package/react-quiz-component) [![License](https://img.shields.io/npm/l/react-quiz-component.svg)](https://github.com/wingkwong/react-quiz-component/blob/master/LICENSE) [![Total NPM Download](https://img.shields.io/npm/dt/react-quiz-component.svg)](https://www.npmjs.com/package/react-quiz-component)

react-quiz-component is a ReactJS component allowing users to attempt a quiz.

## Features

- JSON-based input
- Quiz landing page showing title, synopsis and number of questions
- Quiz Input Validator
- Multiple answers with single correct answer
- Multiple answers with multiple correct answers
- Support text and photo answers
- Continue till answered correctly
- Show explainations when answered correctly or not
- Quiz result page at the end with the dropdown filtering all questions or only those you answered correctly or incorrectly
- Support custom result page
- Return quiz summary at the page
- Allow Instant feedback
- Allow retry until the answer is selected correctly
- Allow markdown in Question
- Allow Picture in Question
- Scoring System

## Installing

```
npm i react-quiz-component
```

## Importing react-quiz-component

```
import Quiz from 'react-quiz-component';
```

## Defining Your Quiz Source

The quiz source is a JSON object. You can use [react-quiz-form](https://github.com/wingkwong/react-quiz-form/) to generate it.

```javascript

```

### Locale Customization

If you want to use your customized text, you can add appLocale into your quiz source. Below is the default one. <questionLength> and <correctIndexLength> will be replaced dynamically.

```javascript
 "appLocale": {
    "landingHeaderText": "<questionLength> Questions",
    "question": "Question",
    "startQuizBtn": "Start Quiz",
    "resultFilterAll": "All",
    "resultFilterCorrect": "Correct",
    "resultFilterIncorrect": "Incorrect",
    "prevQuestionBtn": "Prev",
    "nextQuestionBtn": "Next",
    "resultPageHeaderText": "You have completed the quiz. You got <correctIndexLength> out of <questionLength> questions."
  }
```

## Passing to Quiz container

```javascript
 import { quiz } from './quiz';
 ...
 <Quiz quiz={quiz}/>
```

## Shuffling question set

```javascript
 import { quiz } from './quiz';
 ...
 <Quiz quiz={quiz} shuffle={true}/>
```

## Disabling Default Result Page

```javascript
 import { quiz } from './quiz';
 ...
 <Quiz quiz={quiz} showDefaultResult={false}/>
```

## Enabling Custom Result Page

- In order to enable custom result page, showDefaultResult has to be false.

```javascript
 import { quiz } from './quiz';
 ...
  const renderCustomResultPage = (obj) => {
    console.log(obj);
    return (
      <div>
        This is a custom result page. You can use obj to render your custom result page
      </div>
    )
  }
 ...
  <Quiz quiz={quiz} showDefaultResult={false} customResultPage={renderCustomResultPage}/>
```

## Enabling onComplete Action

```javascript
 import { quiz } from './quiz';
 ...
  const setQuizResult = (obj) => {
    console.log(obj);
    // YOUR LOGIC GOES HERE
  }
 ...
  <Quiz quiz={quiz} showDefaultResult={false} onComplete={setQuizResult}/>
```

## Example of Quiz Summary returned to customResultPage and onComplete

```
Object
  numberOfCorrectAnswers: 4
  numberOfIncorrectAnswers: 1
  numberOfQuestions: 5
  questions: Array(5)
    0: {question: "Which of the following concepts is/are key to ReactJS?", questionType: "text", answers: Array(3), correctAnswer: "3", messageForCorrectAnswer: "Correct answer. Good job.", …}
    1: {question: "ReactJS is developed by _____?", questionType: "text", answers: Array(2), correctAnswer: "2", messageForCorrectAnswer: "Correct answer. Good job.", …}
    2: {question: "How can you access the state of a component from inside of a member function?", questionType: "text", answers: Array(4), correctAnswer: "3", messageForCorrectAnswer: "Correct answer. Good job.", …}
    3: {question: "Lorem ipsum dolor sit amet, consectetur adipiscing elit,", questionType: "photo", answers: Array(4), correctAnswer: "1", messageForCorrectAnswer: "Correct answer. Good job.", …}
    4: {question: "ReactJS is an MVC based framework?", questionType: "text", answers: Array(2), correctAnswer: "2", messageForCorrectAnswer: "Correct answer. Good job.", …}
  userInput: (5) [1, 2, 1, 2, 3]
  totalPoints: 100
  correctPoints: 40

```

## Showing Instant Feedback

```javascript
 import { quiz } from './quiz';
 ...
  <Quiz quiz={quiz} showInstantFeedback={true}/>
```

## Answering the same question till it is correct

```javascript
 import { quiz } from './quiz';
 ...
  <Quiz quiz={quiz} continueTillCorrect={true}/>
```

## Props

| Name                |    Type    | Default | Required | Description                                                                                                  |
| :------------------ | :--------: | :-----: | :------- | :----------------------------------------------------------------------------------------------------------- |
| quiz                |  `object`  | `null`  | Y        | Quiz Json Object                                                                                             |
| shuffle             | `boolean`  | `false` | N        | Shuffle the questions                                                                                        |
| showDefaultResult   | `boolean`  | `true`  | N        | Show the default result page                                                                                 |
| customResultPage    | `function` | `null`  | N        | A quiz summary object will be returned to the function and users can use it to render its custom result page |
| onComplete          | `function` | `null`  | N        | A quiz summary object will be returned to the function                                                       |
| showInstantFeedback | `boolean`  | `false` | N        | Show instant feedback when it is true                                                                        |
| continueTillCorrect | `boolean`  | `false` | N        | Continue to select an answer until it is correct                                                             |
| onQuestionSubmit    | `function` | `null`  | N        | A user response for a question will be returned                                                              |
| disableSynopsis     | `boolean`  | `false` | N        | Disable synopsis before quiz                                                                                 |

## Contribution

- Clone the repository
- Run `npm install`
- Run `npm run dev`
- Run `npm run lint`
- Make a PR to `develop` and describe the changes

## Demo

The demo is available at https://wingkwong.github.io/react-quiz-component/

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
