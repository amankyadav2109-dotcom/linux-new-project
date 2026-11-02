# LIBRARY BOOK INVENTORY AND SEARCH SYSTEM

# 1. Create project folders
mkdir -p Library_Inventory/data Library_Inventory/reports
cd Library_Inventory

# 2. Create files
touch data/books.txt
touch data/available.txt
touch data/issued.txt
touch reports/sorted_books.txt
touch reports/final_inventory.txt

# 3. Enter book records
cat > data/books.txt << EOF
B101,The Alchemist,Paulo Coelho,Fiction,Available
B102,Atomic Habits,James Clear,Self-help,Issued
B103,Computer Networks,Tanenbaum,Technology,Available
B104,Rich Dad Poor Dad,Robert Kiyosaki,Finance,Available
B105,The Hobbit,J.R.R. Tolkien,Fiction,Issued
B106,Python Basics,Reema Thareja,Technology,Available
B107,Ikigai,Hector Garcia,Self-help,Available
B108,DBMS Concepts,Korth,Technology,Issued
B109,The Diary of a Young Girl,Anne Frank,Biography,Available
B110,Wings of Fire,A.P.J. Abdul Kalam,Biography,Issued
EOF

# 4. Display complete book catalogue
echo "===== ALL BOOKS ====="
cat data/books.txt

# 5. Separate available and issued books
grep ',Available$' data/books.txt > data/available.txt
grep ',Issued$' data/books.txt > data/issued.txt

echo "===== AVAILABLE BOOKS ====="
cat data/available.txt

echo "===== ISSUED BOOKS ====="
cat data/issued.txt

# 6. Search for a book title
echo "===== SEARCH BOOK ====="
grep -i "alchemist" data/books.txt

# 7. Search by category
echo "===== TECHNOLOGY BOOKS ====="
grep ",Technology," data/books.txt

# 8. Extract book titles
echo "===== BOOK TITLES ====="
cut -d ',' -f2 data/books.txt

# 9. Search multiple categories
echo "===== FICTION AND TECHNOLOGY BOOKS ====="
egrep ",(Fiction|Technology)," data/books.txt

# 10. Fixed text search
echo "===== FIXED STRING SEARCH ====="
fgrep "Atomic Habits" data/books.txt

# 11. Sort books alphabetically by title
sort -t ',' -k2,2 data/books.txt > reports/sorted_books.txt

echo "===== SORTED BOOKS ====="
cat reports/sorted_books.txt

# 12. Display first three records
echo "===== FIRST THREE BOOKS ====="
head -n 3 reports/sorted_books.txt

# 13. Display last three records
echo "===== LAST THREE BOOKS ====="
tail -n 3 reports/sorted_books.txt

# 14. Combine available and issued books
cat data/available.txt data/issued.txt > reports/final_inventory.txt

echo "===== FINAL INVENTORY REPORT ====="
cat reports/final_inventory.txt

# 15. Change file permissions
chmod 640 reports/final_inventory.txt

# 16. Display project files
echo "===== PROJECT FILES ====="
ls
ls data
ls reports

# 17. Display final folder structure
echo "===== COMPLETE PROJECT STRUCTURE ====="
find . -type f

# PROJECT COMPLETED
echo "===== LIBRARY INVENTORY PROJECT COMPLETED SUCCESSFULLY ====="
