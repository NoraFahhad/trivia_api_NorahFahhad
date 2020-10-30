# # Full Stack API Final Project
## Full Stack Trivia

This project was implemented for Udacity's Full Stack Developer Nano Degree course.


Trivia app about seeing who's the most knowledgeable of the bunch by playing quizzes on different topics. 
The application will:

1) Display questions - all questions and by category.
2) Can show/hide the answer.
3) Delete questions.
4) Add questions.
5) Search for questions.
6) Play the quiz game, randomizing either all questions or within a specific category.


## Getting Started

### Prerequisites & Installation
Developers using this project should already have Python3, pip, node, and npm installed.

### Backend

- recommend working within a virtual environment whenever using Python for projects.
[python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/

- Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

- With Postgres running, restore a database using the trivia.psql file provided. From the backend folder in terminal run:

```bash
psql trivia < trivia.psql
```

- From within the `backend` directory first ensure you are working using your created virtual environment. To run the server, execute:

```bash
export FLASK_APP=flaskr
export FLASK_ENV=development
flask run
```

- Testing setup 

To run the tests, run
```
dropdb trivia_test
createdb trivia_test
psql trivia_test < trivia.psql
python test_flaskr.py
```

### Frontend

- Installing Node and NPM
from [https://nodejs.com/en/download](https://nodejs.org/en/download/).

- Installing project dependencies

```bash
npm install
```

- Running Your Frontend in Dev Mode

```bash
npm start
```

## API Reference

### Getting Started

- Base URL: Currently this application is only hosted locally. The backend is hosted at http://127.0.0.1:5000/
- Authentication: This version does not require authentication or API keys.

### Error Handling
Errors are returned as JSON in the following format:
```bqsh
{
    "success": False,
    "error": 404,
    "message": "resource not found"
}
```

- The API will return three types of errors:

1) 405 – Method not allowed
2) 404 – resource not found
3) 422 – unprocessable

### Endpoints

#### GET /categories
 - General: Returns a list categories objects, and success value.

 - Sample: curl http://127.0.0.1:5000/categories
 ```bash
{
  "categories": {
    "1": "Science", 
    "2": "Art", 
    "3": "Geography", 
    "4": "History", 
    "5": "Entertainment", 
    "6": "Sports"
  }, 
  "success": true
}
```

### GET /questions

- General:
1) Returns a list of questions objects.
2) Results are paginated in pages of 10.
3) In Addition returns list of categories and total number of questions.

- Sample: curl http://127.0.0.1:5000/questions

```bash
{
  "categories": {
    "1": "Science", 
    "2": "Art", 
    "3": "Geography", 
    "4": "History", 
    "5": "Entertainment", 
    "6": "Sports"
  }, 
  "questions": [
    {
      "answer": "Tom Cruise", 
      "category": 5, 
      "difficulty": 4, 
      "id": 4, 
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    }, 
    {
      "answer": "Maya Angelou", 
      "category": 4, 
      "difficulty": 2, 
      "id": 5, 
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    }, 
    {
      "answer": "Muhammad Ali", 
      "category": 4, 
      "difficulty": 1, 
      "id": 9, 
      "question": "What boxer's original name is Cassius Clay?"
    }, 
    {
      "answer": "Brazil", 
      "category": 6, 
      "difficulty": 3, 
      "id": 10, 
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    }, 
    {
      "answer": "Uruguay", 
      "category": 6, 
      "difficulty": 4, 
      "id": 11, 
      "question": "Which country won the first ever soccer World Cup in 1930?"
    }, 
    {
      "answer": "George Washington Carver", 
      "category": 4, 
      "difficulty": 2, 
      "id": 12, 
      "question": "Who invented Peanut Butter?"
    }, 
    {
      "answer": "Lake Victoria", 
      "category": 3, 
      "difficulty": 2, 
      "id": 13, 
      "question": "What is the largest lake in Africa?"
    }, 
    {
      "answer": "The Palace of Versailles", 
      "category": 3, 
      "difficulty": 3, 
      "id": 14, 
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }, 
    {
      "answer": "Agra", 
      "category": 3, 
      "difficulty": 2, 
      "id": 15, 
      "question": "The Taj Mahal is located in which Indian city?"
    }, 
    {
      "answer": "Escher", 
      "category": 2, 
      "difficulty": 1, 
      "id": 16, 
      "question": "Which Dutch graphic artist\u2013initials M C was a creator of optical illusions?"
    }
  ], 
  "success": true, 
  "total_questions": 22
}
```

### DELETE /questions/<int:id>

- General:

1) Deletes a question.
2) Returns questions , id of deleted question and total questions.

- Sample: curl http://127.0.0.1:5000/questions/6 -X DELETE

```bash
{
  "deleted": 97, 
  "questions": [
    {
      "answer": "Tom Cruise", 
      "category": 5, 
      "difficulty": 4, 
      "id": 4, 
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    }, 
    {
      "answer": "Maya Angelou", 
      "category": 4, 
      "difficulty": 2, 
      "id": 5, 
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    }, 
    {
      "answer": "Muhammad Ali", 
      "category": 4, 
      "difficulty": 1, 
      "id": 9, 
      "question": "What boxer's original name is Cassius Clay?"
    }, 
    {
      "answer": "Brazil", 
      "category": 6, 
      "difficulty": 3, 
      "id": 10, 
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    }, 
    {
      "answer": "Uruguay", 
      "category": 6, 
      "difficulty": 4, 
      "id": 11, 
      "question": "Which country won the first ever soccer World Cup in 1930?"
    }, 
    {
      "answer": "George Washington Carver", 
      "category": 4, 
      "difficulty": 2, 
      "id": 12, 
      "question": "Who invented Peanut Butter?"
    }, 
    {
      "answer": "Lake Victoria", 
      "category": 3, 
      "difficulty": 2, 
      "id": 13, 
      "question": "What is the largest lake in Africa?"
    }, 
    {
      "answer": "The Palace of Versailles", 
      "category": 3, 
      "difficulty": 3, 
      "id": 14, 
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }, 
    {
      "answer": "Agra", 
      "category": 3, 
      "difficulty": 2, 
      "id": 15, 
      "question": "The Taj Mahal is located in which Indian city?"
    }, 
    {
      "answer": "Escher", 
      "category": 2, 
      "difficulty": 1, 
      "id": 16, 
      "question": "Which Dutch graphic artist\u2013initials M C was a creator of optical illusions?"
    }
  ], 
  "success": true, 
  "total_questions": 21
}
```

### POST /questions

- General:
1) Creates a new question
2) Returns JSON object with newly created question.
- Sample: curl http://127.0.0.1:5000/questions -X POST -H "Content-Type: application/json" -d '{ "question": "What is the capital city of Saudi Arabia?", "answer": "Riyadh", "difficulty": 3, "category": "3" }'

```bash
{
  "created": 101, 
  "questions": [
    {
      "answer": "Tom Cruise", 
      "category": 5, 
      "difficulty": 4, 
      "id": 4, 
      "question": "What actor did author Anne Rice first denounce, then praise in the role of her beloved Lestat?"
    }, 
    {
      "answer": "Maya Angelou", 
      "category": 4, 
      "difficulty": 2, 
      "id": 5, 
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    }, 
    {
      "answer": "Muhammad Ali", 
      "category": 4, 
      "difficulty": 1, 
      "id": 9, 
      "question": "What boxer's original name is Cassius Clay?"
    }, 
    {
      "answer": "Brazil", 
      "category": 6, 
      "difficulty": 3, 
      "id": 10, 
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    }, 
    {
      "answer": "Uruguay", 
      "category": 6, 
      "difficulty": 4, 
      "id": 11, 
      "question": "Which country won the first ever soccer World Cup in 1930?"
    }, 
    {
      "answer": "George Washington Carver", 
      "category": 4, 
      "difficulty": 2, 
      "id": 12, 
      "question": "Who invented Peanut Butter?"
    }, 
    {
      "answer": "Lake Victoria", 
      "category": 3, 
      "difficulty": 2, 
      "id": 13, 
      "question": "What is the largest lake in Africa?"
    }, 
    {
      "answer": "The Palace of Versailles", 
      "category": 3, 
      "difficulty": 3, 
      "id": 14, 
      "question": "In which royal palace would you find the Hall of Mirrors?"
    }, 
    {
      "answer": "Agra", 
      "category": 3, 
      "difficulty": 2, 
      "id": 15, 
      "question": "The Taj Mahal is located in which Indian city?"
    }, 
    {
      "answer": "Escher", 
      "category": 2, 
      "difficulty": 1, 
      "id": 16, 
      "question": "Which Dutch graphic artist\u2013initials M C was a creator of optical illusions?"
    }
  ], 
  "success": true, 
  "total_questions": 22
}
```

### POST /questions/search


- General:

1) Searches for questions using search term.

- Sample: curl http://127.0.0.1:5000/questions/search -X POST -H "Content-Type: application/json" -d '{"searchTerm": "team"}'
```bash
{
  "questions": [
    {
      "answer": "Brazil", 
      "category": 6, 
      "difficulty": 3, 
      "id": 10, 
      "question": "Which is the only team to play in every soccer World Cup tournament?"
    }
  ], 
  "success": true, 
  "total_questions": 1
}
```

### GET /categories/<int:id>/questions

- General:
1) Gets questions by category.
2) Sample: curl http://127.0.0.1:5000/categories/4/questions

```bash
{
  "questions": [
    {
      "answer": "Maya Angelou", 
      "category": 4, 
      "difficulty": 2, 
      "id": 5, 
      "question": "Whose autobiography is entitled 'I Know Why the Caged Bird Sings'?"
    }, 
    {
      "answer": "Muhammad Ali", 
      "category": 4, 
      "difficulty": 1, 
      "id": 9, 
      "question": "What boxer's original name is Cassius Clay?"
    }, 
    {
      "answer": "George Washington Carver", 
      "category": 4, 
      "difficulty": 2, 
      "id": 12, 
      "question": "Who invented Peanut Butter?"
    }, 
    {
      "answer": "Scarab", 
      "category": 4, 
      "difficulty": 4, 
      "id": 23, 
      "question": "Which dung beetle was worshipped by the ancient Egyptians?"
    }
  ], 
  "success": true
}
```

### POST /quizzes

- General:
1) user can play the quiz.

- Sample: curl http://127.0.0.1:5000/quizzes -X POST -H "Content-Type: application/json" -d '{"previous_questions": [5, 9], "quiz_category": {"type": "History", "id": "4"}}'

```bash
{
  "question": {
    "answer": "Scarab", 
    "category": 4, 
    "difficulty": 4, 
    "id": 23, 
    "question": "Which dung beetle was worshipped by the ancient Egyptians?"
  }, 
  "success": true
}
```

## Authors

Norah Alnujaym for (__init__.py), (test_flaskr.py), and README.

## Acknowledgements

The awesome Coach Caryn
