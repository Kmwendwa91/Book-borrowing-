 import from datetime import datetime

book_info = {
    "bookID": input("Enter Book ID: "),
    "dueDate": input("Enter Due Date (YYYY-MM-DD): "),
    "returnDate": input("Enter Return Date (YYYY-MM-DD): ")
}

dueDate = datetime.strptime(book_info['dueDate'], "%Y-%m-%d")
returnDate = datetime.strptime(book_info['returnDate'], "%Y-%m-%d")

daysOverdue = (returnDate - dueDate).days
fineRate = 0 if daysOverdue <= 0
 else 20 if daysOverdue <= 7
 else 50 if daysOverdue <= 14 
else 100
fineAmount = max(daysOverdue, 0) * fineRate

book_info.update({
    "daysOverdue": daysOverdue,
    "fineRate": fineRate,
    "totalFineAmount": fineAmount
})

for key, value in book_info.items():
    print(f"{key}: {value}")
