To update the seating chart:
    1. Update SeatingChart.xlsx
    2. Run both cells in seatingChartConversion.ipynb
        - Use Ctrl+Enter twice or "Run all" button
    3. Copy all the text in chartHelper.txt 
        - Use Ctrl+A to select all and Ctrl+C to copy 
    4. Paste the text at the top of seatingChart.js
        - Delete any pre-existing text between the comment lines
    5. Re-order names as needed for political correctness (see below for details)
    6. Open a terminal and navigate to seatingChartApp folder
        - Ctrl+K+O in VSCode or "cd [insert filepath]" in command line 
    7. Deploy updates to server:
            git add -A 
            git commit -m "[insert description of changes]"
            git push


Order of listing
    - Within each table, the order of people in seatingChart.js is the order they will appear in on the website 
    - Ex. If Vishay Chudgar should be listed above Shaan Chudgar at the same table, make sure seatingChart.set("Vishay Chudgar", [#]); 
        is above seatingChart.set("Shaan Chudgar", [#]);
        

Multiple guests with the same name 
    - Ex. Two Smita Shahs (one at Table 5 and one at Table 8)
    - By default, chartHelper.txt has one line for Smita Shah, placed with the other Table 5 people

            seatingChart.set("Nitin Shah", [5]);
            seatingChart.set("Tripal Shah", [5]);
            seatingChart.set("Hardik Shah", [5]);
            seatingChart.set("Swati Shah", [5]);
            seatingChart.set("Bela Thakkar", [5]);
            seatingChart.set("Jashvant Thakkar", [5]);
            seatingChart.set("Jashwant Shah", [5]);
            seatingChart.set("Smita Shah", [5, 8]);
            seatingChart.set("Nandu Shah", [5]);
            seatingChart.set("Yojana Shah", [5]);
            ...
            seatingChart.set("Siren Chudgar", [8]);
            seatingChart.set("Jennifer Chudgar", [8]);
            seatingChart.set("Mayank Shah", [8]);

    - Problem: On the website, Smita Shah of Table 8 is listed as the first person at that table (above Siren Chudgar)
            Table 5
            =======
            Nitin Shah
            Tripal Shah
            Hardik Shah
            Swati Shah
            Bela Thakkar
            Jashvant Thakkar
            Jashwant Shah
            Smita Shah
            Nandu Shah
            Yojana Shah

            Table 8
            =======
            Smita Shah
            Siren Chudgar
            Jennifer Chudgar
            Mayank Shah 
            ...

    - Solution: Take anyone at Table 8 who should be listed before Smita, and paste them above all of Table 5

            seatingChart.set("Siren Chudgar", [8]);
            seatingChart.set("Jennifer Chudgar", [8]);
            seatingChart.set("Mayank Shah", [8]);

            seatingChart.set("Nitin Shah", [5]);
            seatingChart.set("Tripal Shah", [5]);
            seatingChart.set("Hardik Shah", [5]);
            seatingChart.set("Swati Shah", [5]);
            seatingChart.set("Bela Thakkar", [5]);
            seatingChart.set("Jashvant Thakkar", [5]);
            seatingChart.set("Jashwant Shah", [5]);
            seatingChart.set("Smita Shah", [5, 8]);
            seatingChart.set("Nandu Shah", [5]);
            seatingChart.set("Yojana Shah", [5]);

    - Results: Both Smita Shahs are listen in appropriate order
            Table 5
            =======
            Nitin Shah
            Tripal Shah
            Hardik Shah
            Swati Shah
            Bela Thakkar
            Jashvant Thakkar
            Jashwant Shah
            Smita Shah
            Nandu Shah
            Yojana Shah

            Table 8
            =======
            Siren Chudgar
            Jennifer Chudgar
            Mayank Shah 
            Smita Shah
            ...