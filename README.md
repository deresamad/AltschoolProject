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

## to_dict: Returns a dictionary representation of the expense.


   

