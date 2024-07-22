# Introduction 
Compare JK Rowling's object and subject frequencies for feminine and masculine personal pronouns when she is writing as herself or her pseudonym, Robert Galbraith.  

# Methodology
1. I will download comparable number of words between her Harry Potter series and her "Robert Galbraith" books 
    - pre-2013 because that is when she was outed (NPR, 2015). 
    - Find PDFs
        - The Cuckoo's Calling (https://worldfabibooks.wordpress.com/wp-content/uploads/2013/10/the-cuckoo_s-calling-robert-galbraith-j-k-rowling.pdf)
            - downloaded pgs 7-384
            - used https://www.pdfagile.com/online/pdf-to-txt to convert to txt
            - find line count ("wc -l cuckoos_calling_text.txt") = 16373
        - Harry Potter and the Sorcerer's Stone (https://docenti.unimc.it/antonella.pascali/teaching/2018/19055/files/ultima-lezione/harry-potter-and-the-philosophers-stone)
            - downloaded 2-250
            - repeat steps above
            - line count = 11113
        <!-- - Harry Potter and the Chamber of Secrets (https://www.hasanboy.uz/wp-content/uploads/2018/04/Harry-Potter-and-the-Chamber-of-Secrets.pdf)
            - downloaded 7-251
            - repeated steps above
            - line count = 10085 -->
        - Harry Potter and the Deathly Hallows (https://vidyaprabodhinicollege.edu.in/VPCCECM/ebooks/ENGLISH%20LITERATURE/Harry%20potter/(Book%207)%20Harry%20Potter%20And%20The%20Deathly%20Hallows.pdf)
            - chose this one because closest in time to release date of Cuckoo's Calling
            - downloaded 7-767
            - repeat steps above
            - line count = 24320
    - used flesch reading score to determine reading level
        - on scale of 1-100
        - used https://readabilityformulas.com/readability-scoring-system.php
        - uploaded txt files that reduced it to 3500 words
        - had it process random sample
        - repeated 3x, found avg 
            - Cuckoo's Calling = 66.67 (avg)
                - 59 (test 1)
                - 64 (test 2)
                - 77 (test 3)
            - HP 1 = 81.33 (avg)
                - 79 (test 1)
                - 87 (test 2)
                - 78 (test 3)
            <!-- - HP 2 = 76 (avg)
                - 77 (test 1)
                - 76 (test 2)
                - 75 (test 3) -->
            - HP 7 = 76 (avg)
                - 77 (test 1)
                - 76 (test 2)
                - 75 (test 3)
    - have to get standard scale it somehow. adjust for number of words in proportion to reading level
        - normalize to cuckoo's calling 
            - use only 7500 lines so that don't have to use all of any of the books
            - normalize 66.67 reading level to 7,500 lines
        - HP 1
            - 66.67/7,500 = 81.33/x
            - x = 9,149 lines
        <!-- - HP2? -->
        - HP 7 
            - 66.67/7,500 = 76/x
            - x = 8,550 lines
2. SparkNLP and PoS
    - randomize the lines chosen using random.sample()
    - set seed so it is reproducible
    - find parts of speech for the given lines
    - filter for just pronouns
    - make dataframe for their frequencies
3. Statistics
    - review R notes to see which test to use for comparing proportions


# Hypothesis
I hypothesize that JK Rowling has more patriarchical object and subject frequencies in her writing both when she is writing as a male and as time progressed.


# Evaluation


# Conclusion


# Works Cited
1. NPR. (2015, November 2). *J.K. Rowling On Her Nom De Plume Robert Galbraith* NPR. https://www.npr.org/2015/11/02/453885684/j-k-rolling-on-her-nom-de-plume-robert-galbraith#:~:text=She%20was%20outed%20back%20in,very%20real%20person%20to%20me.