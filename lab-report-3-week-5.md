# Lab Report 3 

**I chose to explore the grep command.**


The first command-line option would be -c which prints only the count of the lines that match a pattern.
 

(The find-results.txt file contains the output of running find technical/)
```
[cs15lfa22ln@ieng6-202]:docsearch:124$ grep -c ".txt" find-results.txt
1391
```
This is finding all instances of .txt in the directory and returns how many times it finds it. This is useful as a way to see how many .txt files there are. 


```
[cs15lfa22ln@ieng6-202]:docsearch:128$ grep -c "/plos" find-results.txt
253
```
This is finding all instances of /plos in the directory and returns how many times it finds it. This is useful as a way to see how many files there are under the plos subdirectory. 

```
[cs15lfa22ln@ieng6-202]:docsearch:127$ grep -c "legal" find-results.txt
5
```
This is finding all instances of legal in the directory and returns how many times it finds it. This is useful as a way to see how many files have the name legal in in them. 



The second command-line option would be -i which ignores case for matching.


```
[cs15lfa22ln@ieng6-202]:docsearch:141$ grep -i "bMi" technical/biomed/1468-6708-3-1.txt
        between body mass index (BMI) and mortality, controlling
        excess risk for persons with very low BMI, but that persons
        with moderately high BMI had little or no extra risk except
        because few studies have examined the relation of BMI to
        events [ 10 ] . In this paper we study whether BMI at
          BMI was calculated as measured weight in kilograms
          BMI of 18.5 to 24.9; overweight as 25 to 29.9; and
          separately the group with BMI between 18.5 and 20, which
          with BMI. To adjust for possible confounding we chose
          and likely to be related to BMI. Self-reported covariates
          plotted mean adjusted YOL and YHL against BMI, and tested
          for difference among BMI groups using confidence
          the effect size for each measure, comparing each BMI
        smokers. Black women had a higher mean BMI and higher
        percent obese (BMI ≥ 30) than the other three groups. Black
        statistically significant (p <.05) except for BMI and
        significant differences between black and white for BMI,
        the difference in BMI was no longer statistically
        significantly on BMI, BMI>30, weight loss since age 50,
        We next examined the relationship of BMI to YOL and YHL.
        BMI below 18.5, but averaged 6.6 years for women with a BMI
        only discrepancy is for men with BMI < 18.5, a category
        with BMI from 18.5 to 20 would be considered 'normal' by
        increase sample size for those with low BMI, we combined
        the two lower categories, defining underweight as a BMI
        BMI. For each BMI category the mean and its 95% confidence
        between BMI and YOL for BMI above 20. Underweight women
        normal group. The relationship of BMI to YHL for men is
        similar, but differences among BMI groups were not
        to the normal BMI group. The effect sizes are shown in
          et al proposed a desirable BMI of
        BMI Body mass index
```
This is searching through the contents of the technical/biomed/1468-6708-3-1.txt file for any instances of BMI regardless of case. This is useful since it can search for the acronym even if the user forgets to capitalize some of the letters. 

```
[cs15lfa22ln@ieng6-202]:docsearch:142$ grep -i "eVgfP" technical/biomed/1468-6708-3-1.txt
          good, fair, or poor?) (EVGFP) which was collected every 6
          months. EVGFP is a simple but well-known measure, which
          value to each level of EVGFP [ 19 ] . Preliminary results
        thus substantial change in EVGFP over time, in both
        from EVGFP) in the first seven years of the study, adjusted
          EVGFP, on which YHL was based, might have missed some
          pain would surely have worse EVGFP than others, based on
          be more sensitive to change in weight than EVGFP. If YHL
          of any differences in EVGFP.
        EVGFP Is your health excellent, very good, good, fair or
```

This is searching through the contents of the technical/biomed/1468-6708-3-1.txt file for any instances of EVGFP regardless of case. This is useful since it can search for the acronym even if the user forgets to capitalize some of the letters. 

```
[cs15lfa22ln@ieng6-202]:docsearch:144$ grep -i "Cesd" technical/biomed/1468-6708-3-1.txt
          depression (CESD score), serum albumin, serum
        CESD Center for Epidemiologic Studies Depression
```
This is searching through the contents of the technical/biomed/1468-6708-3-1.txt file for any instances of CESD regardless of case. This is useful since it can search for the acronym even if the user forgets to capitalize some of the letters.  



The third command-line option would be -n which displays the matched lines and their line numbers.


```
[cs15lfa22ln@ieng6-202]:docsearch:150$ grep -n "impact" technical/plos/journal.pbio.0020001.txt
122:        What, exactly, is the relative impact of such developing regions as Latin America on the
128:        Science ; with impact factors of 27.96 and 23.33, respectively) and in
129:        the 20 top ecological journals (with impact factors of 10.51–2.47) (ISI 2001a). We credited
138:        data as contributions to the top 10 ecological journals (impact factors 10.51–3.31) versus
139:        the top 11–20 (impact factors 3.28–2.47), the Latin American countries contributed nearly
167:        impact in the international scientific community and is underrepresented in the top
203:        areas of concern that are having a proportionally greater scientific and social impact upon
226:        target the journals that have the greatest impact. Although there may still be a long road
```

This is searching through the contents of the technical/plos/journal.pbio.0020001.txt file for any instances of impact and prints out which line it came from and the corresponding line. This is useful since it can pinpoint where in the text that specific word is located. 

```
[cs15lfa22ln@ieng6-202]:docsearch:152$ grep -n "science" technical/plos/journal.pbio.0020001.txt
7:        the clear inequalities in science between developing and developed countries and to the
10:        importance of reducing the inequalities in science between developed and developing
29:        It is rather obvious that richer countries are able to invest more resources in science
75:        contributions to science, despite the fact that the average proportion of gross domestic
76:        product (GDP) invested in science in Latin America throughout this 10-year period was only
78:        productivity is remarkable when we compare it with the relatively low investment in science
85:        rate as well as in financial investment in science and technology. Some countries have
112:        funding to the most productive scientists from the national science development programs
125:        and global change biology) between 1990 and 2002 in both the two top general science
158:        American researchers are not shying away from the two top-ranked general science journals.
163:        ecology and environmental sciences emphasizes the overwhelming contributions of authors
178:        conspiracy, but rather it implies that the perception of the most important science is
181:        science is most interesting to them. Another consideration is that more local journals from
196:        developing world (Goldemberg 1998; Annan 2003). One is that science, as a discipline, would
207:        Brazil (Goldemberg 1998) and biomedical sciences in Cuba (Castro Díaz-Balart 2002). These
224:        to the sciences will be an excellent investment by developing nations in terms of
```

This is searching through the contents of the technical/plos/journal.pbio.0020001.txt file for any instances of science and prints out which line it came from and the corresponding line. This is useful since it can pinpoint where in the text that specific word is located. The number of the lines the word is located can also give a sense of the distribution of the word in the article.

```
[cs15lfa22ln@ieng6-202]:docsearch:153$ grep -n "biodiversity" technical/plos/journal.pbio.0020001.txt
200:        Climate change and biodiversity research, for example, urgently need the scientific input
213:            Climate change and biodiversity research urgently need the scientific
```

This is searching through the contents of the technical/plos/journal.pbio.0020001.txt file for any instances of biodiversity and prints out which line it came from and the corresponding line. This is useful since it can pinpoint where in the text that specific word is located and how many lines. 