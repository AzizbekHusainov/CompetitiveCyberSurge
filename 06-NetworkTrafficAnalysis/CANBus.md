# Tools used: Wireshark and Excel Spreadsheets
# Process the Data using Wireshark
1. Select one of the data lines after opening the file from Cyber Skyline through Wireshark.
2. On the bottom left window, navigate to find and `ID` line.
3. Right click and select apply as column.
4. Now navigate to the Data section in the bottom left window and look for `Data` line.
5. Right click and select apply as column.
6. Now select File, export file dissections, and export as csv file.

# Process the CSV file using Excel (or any other spreadsheets software)
1. Open the file.
2. Ensure the ID and Data columns are visible.
3. Press Ctrl + a to select all data and insert a pivot table.
4. Count the number of distinct IDs for question 1 (You can use excel functions such as counta() to make it easier to count).
5. For question two, we will be looking for instances of CAN ID 589 because according to the code, ID 589 is responsible for speed: `int speed_id = 589; if (frame.can_id == speed_id)`
6. We can do the previous step by using excel function, `=COUNTIF(F:F,589)`
7. For step 3, we want to look at the code to understand how speed is obtained. From the code we deduce that `mph = ((byte3 * 256 + byte4) / 100) * 0.6213751`
8. We can use this excel command to compute speed `=IF(G2=589, ((HEX2DEC(MID(H2,7,2))*256 + HEX2DEC(MID(H2,9,2))) / 100) * 0.6213751, "")` in a new column.
9. Drag down from the bottom right of the cell for all entries.
10. In a new cell run the function `=MAX(L:L)` to obtain the highest speed. Note that the characters inside the function change in respect to which column contains the data of interest.

# Answers
1. 36
2. 352
3. 20.13
