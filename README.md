# online-Library-Management-System
Online library management system using  object oriented programming in python

I have to create a library class that includes the following mthods:

Displaybook() : To display the available books
Lendbook(): To lend a book to a user
Addbook(): To add a book to the library
Returnbook(): To return the book to the library.
    
As I have created a library class, then I will create an object and pass the following parameters in the constructor.

HarryLibrary=Library(listofbooks, library_name)

After that, create a main function and run an infinite while loop that asks the users for their input whether they want to display, lend, add or return a book.

Optional:-

Maintain a dictionary for the users who own a book. Dictionary should take book name as a key and name of the person as a value. Whenever you lend a book to a user, you should maintain a dictionary.

 

class Library:

    def __init__(self, list, name):
        self.bookslist = list
        self.name = name
        self.lendDict = {}

    def displayBooks(self):
        print(f" We have following books in our library: {self.name}")
        for book in self.bookslist:
            print(book)

    def lendBook(self, name, book):  # give the book to the students
        if book not in self.lendDict.keys():
            self.lendDict.update({book: name})
            print("Lender-Book database has been updated.You can take the book now")
        else:
            print(f"Book is already being used by  {self.lendDict[book]}")

    def addBook(self, book):
        self.bookslist.append(book)
        print("Book has been added to the book list")

    def returnBook(self, book):
        self.lendDict.pop(book)


if __name__ == '__main__':
    harry = Library(['python', 'Rich dadd and poor dad',
                    'Harry potter', 'c++', 'pandas'], "IGNOU")
    while (True):
        print(
            f"Welcome to the {harry.name} library. Enter your choice to continue")
        print("1.Display Books")
        print("2.Lend a Book")
        print("3. Add a book")
        print("4, Return a Book")
        user_choice = input()
        if user_choice not in ['1', '2', '3', '4']:
            print('please enter a valid option')
            continue
        else:
            user_choice = int(user_choice)

        if user_choice == 1:
            harry.displayBooks()

        elif user_choice == 2:
            book = input("Enter the name of the book you want to lend:")
            name = input("enter your name: ")
            harry.lendBook(name, book)

        elif user_choice == 3:
            book = input("enter  the name of the book you want to add: ")
            harry.addBook(book)

        elif user_choice == 4:
            book = input("Enter the name of the book you want to return: ")
            harry.returnBook(book)
        else:
            print("Not a valid option")

        print(" press q to quit and c to continue")
        user_choice2 = ""

        while (user_choice2 != "c" and user_choice2 != "q"):
            user_choice2 = input()
            if user_choice2 == "q":
                exit()

            if user_choice2 == "c":
                continue
   
        

