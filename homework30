class Book:
    def __init__(self, title, author, year, genre, quantity):
        self.title = title
        self.author = author
        self.year = year
        self.genre = genre
        self.quantity = quantity

    def __str__(self):
        return f"{self.title} ({self.year}) by {self.author}, {self.genre}, {self.quantity} copies available"

    def decrease_quantity(self):
        if self.quantity > 0:
            self.quantity -= 1

    def increase_quantity(self):
        self.quantity += 1


class User:
    def __init__(self, name, user_id):
        self.name = name
        self.user_id = user_id
        self.borrowed_books = []

    def __str__(self):
        return f"{self.name} (ID: {self.user_id})"

    def borrow_book(self, book):
        if book.quantity > 0:
            self.borrowed_books.append(book)
            book.decrease_quantity()

    def return_book(self, book):
        if book in self.borrowed_books:
            self.borrowed_books.remove(book)
            book.increase_quantity()


class Library:
    def __init__(self):
        self.books = []
        self.users = []

    def add_book(self, book):
        self.books.append(book)

    def remove_book(self, book):
        self.books.remove(book)

    def register_user(self, user):
        self.users.append(user)

    def remove_user(self, user):
        self.users.remove(user)

    def lend_book(self, book, user):
        for b in self.books:
            if b.title == book.title:
                b.decrease_quantity()
                user.borrow_book(b)
                break

    def return_book(self, book, user):
        for b in self.books:
            if b.title == book.title:
                b.increase_quantity()
                user.return_book(b)
                break

    def list_available_books(self):
        available_books = []
        for book in self.books:
            if book.quantity > 0:
                available_books.append(book)
        return available_books


class Transaction:
    def __init__(self, date, transaction_type, book, user):
        self.date = date
        self.transaction_type = transaction_type
        self.book = book
        self.user = user

    def __str__(self):
        return f"{self.date}: {self.transaction_type} of {self.book.title} by {self.user.name} (ID: {self.user.user_id})"

    def record_transaction(self):
        print(self)
