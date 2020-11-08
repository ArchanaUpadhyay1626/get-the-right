import csv
seats=[]
seats.append([0,0,1,1,0,1,1,1])
seats.append([0,1,1,0,0,1,0,1])
seats.append([1,0,0,1,0,1,1,0])
seats.append([0,1,1,1,0,0,0,1])
seats.append([0,0,1,1,0,1,0,0])
seats.append([1,0,1,1,0,0,1,1])

def displayBookings():
    print("")
    print("================================================================")
    print("")
    for row in seats:
        print(row)
    print("")
    print("============================================================")
        
def checkSeat():
    row=int(input("Enter a row number (between 0 and 5): "))
    column=int(input("Enter a column number (between 0 and 7): "))
    
    if seats[row][column]==1:
        print("Booked. ")
    else:
        print("Empty. ")
        

def bookSeat():
    print("Booking a seat by row/column. ")
    booked= False
    while booked== False:
        row=int(input("Enter a row number(between 0 and 5):  "))
        column=int(input("Enter a column number(between 0 and 7): "))
        if seats[row][column]==1:
            print("Already Booked. ")
        else:
            print("Empty. ")
            print("Booking seat....")
            seats[row][column]=1
            print("We've booked a seat for you. ")
            print("Thank you!!! ")
            booked=True
    
    
def bookSeatAtFront():
    print("Booking seat at front. ")
    for row in range(0,6):
        for column in range(0,8):
            if seats[row][column]==0:
                print("Booking seat......")
                print("Row: " + str(row))
                print("Column: "+ str(column))
                seats[row][column]=1
                print("We've booked a seat for you.")
                return True
            print("THEATRE FULL. ")
            return False
                
    
    
    
    
def bookSeatAtBack():
    print("Booking seat at back. ")
    for row in range(5,-1,-1):
        for column in range(7,-1,-1):
            if seats[row][column]==0:
                print("Booking seat.......")
                print("Row: " + str(row))
                print("Column: " + str(column))
                seats[row][columns]=1
                print("We've booked a seat for you. ")
                return True
            print("THEATRE FULL. ")
            return False
                
            
def loadBookings():
    file=open("seats.csv","r")
    row=0
    for line in file:
        data=line.split(",")
        if len(data)==8:
            for column in range(0,8):
                seats[row][column]=int(data[column])
            row+=1
    file.close()
    
    
    
def saveBookings():
    file=open("seats.txt","w")
    for row in range(0,6):
        line=""
        for column in range(0,8):
            line=line+str(seats[row][column]) + ","
        line=line[:-1] + "\n"
        file.write(line)
    file.close()
    
    
print("+====================================================+")
print("+    CINEMA BOOKING SYSTEM    +")
print("+====================================================+")
print(" ")
print("1. Book seat by row/column. ")
print("2. Book seat at front. ")
print("3. Book seat at back. ")
print("x- Exit. ")


choice=input("Enter your choice: ")
if choice=='1':
    bookSeat()
    displayBookings()
    
elif choice=='2':
    bookSeatAtFront()
    displayBookings()
    
elif choice=='3':
    bookSeatAtBack()
    displayBookings()
    
elif choice=='x':
    print("Good Bye!!")
    print("Have a nice day. \n Visit Again.")
    
else:
    print("Invalid option. ")
    print("Good Bye!")

    
loadBookings()
saveBookings()

