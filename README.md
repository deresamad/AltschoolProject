# AltschoolProject_ExpenseDB
##  Introduction
The goal of this project is to assess my understanding of object-oriented programming (OOP) concepts in Python. 
The project task is to  implementing two classes, Expense and ExpenseDatabase, to model and manage financial expenses. 

##  Expense class
An expense class represents an individual financial expense. It has a couple of attributes shared by all instances of the expense class.

id: A unique identifier generated as a UUID string.

title: A string representing the title of the expense.

amount: A float representing the amount of the expense.

created_at: A timestamp indicating when the expense was created (UTC).

updated_at: A timestamp indicating the last time the expense was updated (UTC).

```
class Expense:
    def __init__(self,id, title ,amount):  
          self.id = (str(uuid.uuid4()))  
          self.title = title  
          self.amount = amount  
          self.created_at = self.updated_at = self.get_utc_timestamp()
```


 ## Expense class methods
This refers to the different behaviours that objects will show.

Update : a method that updates the title and/or amount of the expense, if they are not None. It also sets the updated_at attribute to the current time using the datetime module.
```
def update(self, title=None, amount=None):
        self.title = title if title is not None else self.title
        self.amount = amount if amount is not None else self.amount
        self.updated_at = self.get_utc_timestamp()
```

## To returns a dictionary representation of the expense.
to_dict: a method that returns a dictionary representation of the expense
```
 def to_dict(self):
        return {
            'id': self.id,
            'title': self.title,
            'amount': self.amount,
            'created_at': self.created_at,
            'updated_at': self.updated_at
        }
```
```
@staticmethod
    def get_utc_timestamp():
        return datetime.utcnow().replace(tzinfo=timezone.utc).isoformat()
```
the get_utc_timestamp method returns the current UTC timestamp as a string in ISO 8601 format.
This is often used for logging or recording the time of an event in a standardized and timezone-aware way.

##  Expense Database Class
The Expense Database class represents a collection of the expenses. 
This database is assigned to an empty list, a list that stores the expenses as objects of the Expense class.
```
class ExpenseDatabase:
    def __init__(self):
        self.expenses = []
```
add_expense: a method that takes an expense object as an argument and appends it to the database list. 
```
def add_expense(self, expense):
        self.expenses.append(expense)
```
remove_expense: a method that takes an id as an argument and removes the expense object with that id from the database list. 
```
 def remove_expense(self, expense_id):
        self.expenses = [exp for exp in self.expenses if exp.id != expense_id]
```
get_expense_by_id: a method that takes an id as an argument and returns a list of expense objects with that id from the database list. If there is none, it returns an empty list.
```
def get_expense_by_id(self, id):
        return[expense for expense in self.database if expense.id == id]
```
get_expense_by_title: a method that takes a title as an argument and returns a list of expense objects with that title from the database list. If there is none, it returns an empty list.
```
 def get_expenses_by_title(self, title):                                                         
        return [expense for expense in self.expenses if expense.title == title]
```

to_dict: a method that returns a list of dictionaries, each representing an expense object in the database list, using the to_dict method of the Expense class.
```
def to_dict(self):
        return [expense.to_dict() for expense in self.expenses]
 ```
##  How to Clone this project
A clone allows you to work with the entire repository, including all the files, branches and commits. You can then push your changes to the remote repository, or pull other people’s changes from the remote repository. However, you cannot contribute to the original repository unless you are a collaborator or you create a pull request.
1.  Click on the “<> Code ” button close to the 'add file' button.
2.  Copy the URL under HTTPS [copy here](https://github.com/deresamad/AltschoolProject)
3.  Open Git Bash on your computer 
4.  Change the current working directory to the location where you want the cloned directory.
5.  Type git clone, and then paste the URL you copied
6.  Press Enter to create your local clone.

 ##  How to run the code
 In order to execute the code,
 1. Ensure python is installad on your desktop
 2. Navigate to the project directory where expense_tracker.py is saved.
 3. Run the python script  `python expense_tracker.py `
    
   




   

