# Introduction 
Compare JK Rowling's object and subject frequencies for feminine and masculine personal pronouns when she is writing as herself or her pseudonym, Robert Galbraith.  


# Methodology
- Gather text files from the books in question.
- Use only a comparable number of lines from each book by normalizing to reading level (using their Flesch Reading Scores).
- Use SparkNLP to find the parts of speech for each word in the lines fed to it.
- Clean datasets and normalize to both the frequency of each pronoun and the baseline book's (Harry Potter and the Sorcerer's Stone) proportion of pronoun part of speech categorization.  


# Hypothesis
I hypothesize that JK Rowling wrote with more patriarchical object and subject frequencies both when she was writing as a male and as time progressed.


# Evaluation
1. Download comparable number of words between her Harry Potter series and books by "Robert Galbraith" 
    - Find PDFs
        - "The Cuckoo's Calling" (https://worldfabibooks.wordpress.com/wp-content/uploads/2013/10/the-cuckoo_s-calling-robert-galbraith-j-k-rowling.pdf)
            - Use only pre-2013 Robert Galbraith books because that is when JK Rowling's pseudonym became common knowledge (NPR, 2015) 
            - Download pgs 7-384
            - Use https://www.pdfagile.com/online/pdf-to-txt to convert to txt
            - Find line count ("wc -l cuckoos_calling_text.txt") = 16373
        - "Harry Potter and the Sorcerer's Stone" (https://docenti.unimc.it/antonella.pascali/teaching/2018/19055/files/ultima-lezione/harry-potter-and-the-philosophers-stone)
            - Use this one as standard to compare others to
            - Download 2-250
            - Repeat steps above
            - Line count = 11113
        - "Harry Potter and the Deathly Hallows" (https://vidyaprabodhinicollege.edu.in/VPCCECM/ebooks/ENGLISH%20LITERATURE/Harry%20potter/(Book%207)%20Harry%20Potter%20And%20The%20Deathly%20Hallows.pdf)
            - Choose this one because closest in time to release date of Cuckoo's Calling
            - Download 7-767
            - Repeat steps above
            - Line count = 24320
    - Use Flesch Reading Score to determine reading level
        - (Reading level is given on a linear scale of 1-100, so it will be easy to adjust line count later.)
        - https://readabilityformulas.com/readability-scoring-system.php
        - Uploaded txt files, which reduces each to 3500 words
        - Process random sample
        - Repeated 3x, found average 
            - Cuckoo's Calling = 66.67 (avg)
                - 59 (test 1)
                - 64 (test 2)
                - 77 (test 3)
            - HP1 = 81.33 (avg)
                - 79 (test 1)
                - 87 (test 2)
                - 78 (test 3)
            - HP7 = 76 (avg)
                - 77 (test 1)
                - 76 (test 2)
                - 75 (test 3)
    - Standard scale by adjusting for number of words in proportion to reading level
        - Normalize to "Cuckoo's Calling"
            - Use only 7500 lines so that don't have to use all of any of the books
            - So normalize 66.67 reading level to 7,500 lines
        - HP1
            - 66.67/7,500 = 81.33/x
            - x = 9,149 lines
        - HP7 
            - 66.67/7,500 = 76/x
            - x = 8,550 lines
2. SparkNLP and PoS
    - Randomize the lines chosen using random.sample()
    - Set seed so it is reproducible
    - Find parts of speech for the given lines
3. Cleaning and "Statistics"
    - Filter for just pronouns
    - Make a dataframe for their frequencies
    - Normalize first to the number of each pronoun used 
        - ex: If "her" was labeled as a PRP 50 times and PRP$ 300 times, then the new values become [50/(50+300)] and [300/(50+300)], respectively.
    - Combine with the other books into one datafame
    - Then normalize to the baseline, "Harry Potter and the Sorcerer's Stone"
    - Eliminate all pronouns where there wasn't a difference across books (where the normalized value is 1.0 for each book).

    - NOTE: Cannot do statistics since only have one result from each condition (eliminating potential tests such as t tests, proportion z tests, tukey, anova, etc) and since it would not be accurate to use count data (eliminating chisq test of homogeneity).
        - Have to use proportion data rather than count data since (1) there are an unequal number of words used and (2) there are far more male characters than female, so the usage would be much higher for traditionally male pronouns and skew the results.


# Conclusion
input visualizations
review what the pos mean
make ppt


# Works Cited
1. NPR. (2015, November 2). *J.K. Rowling On Her Nom De Plume Robert Galbraith* NPR. https://www.npr.org/2015/11/02/453885684/j-k-rolling-on-her-nom-de-plume-robert-galbraith#:~:text=She%20was%20outed%20back%20in,very%20real%20person%20to%20me.
finish this, add superscripts