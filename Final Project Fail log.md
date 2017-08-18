# TEI Final Project Fail Log

Downloaded module3-wrangling data from the Crafting digital history github 
-	In order to retrieve access to the blanktemplate.txt file needed 

I decided to work on Atom – I had previously downloaded the program for a past excerise in HIST3814O

Then I opened up the Shawville Equity data. I went through the data and decided to transcribe the first issue of 1973. I found the issue here http://collections.banq.qc.ca:8008/jrn03/equity/src/1973/01/03/83471_1973-01-03.pdf

I then opened Atom 

Opened the blanktemplate.txt that I zipped from the module3-wrangling three repo in atom 

I then put – 
<biblScope>pp 1-6</biblScope> 

this is to say which pages I will be transcribing, it is a scope of bibliographic reference.

I found the information about biblscope on this website http://www.tei-c.org/release/doc/tei-p5-doc/en/html/examples-publisher.html. After wondering if I would be different than the one we used in module 2, exercise 3. 

I put this text between both “bodys” near the end of the blanktemplate.txt, so all the text I will be transcribing from the Shawville article will be written above the second “body”
 
Started transcribing the text
I then started to markup the text. I used these two markups from Exercise 3, Module 2 of Shawn Graham’s HIST 3814 Workbook: 

## For people: 

<persName key="Last, First" from="YYYY" to="YYYY" role="Occupation" ref="http://www.website.com/webpage.html"> </persName>


## For locations: 

<placeName key="Sheffield, United Kingdom" ref="http://tools.wmflabs.org/geohack/geohack.php?pagename=Sheffield&params=53_23_01_N_1_28_01_W_type:city_region:GB""> </placeName>

I also used the following to markups from Julia Flanders’ Basic Tagging: Introduction to TEI. 

## For people (with no information): 

<persName>Baron Olivier of Brighton</persName>

## For Organisations/Groups: 

<orgName>Podunk Sewing Club</orgName>

Once I finished that, I took the stylesheet from the module3-wrangling data from the Crafting digital history github and made the necessary changes so it went along with my project. I found this change because one my peers, @claremaier, made a post about the stylesheet in our Slack group and @dr.graham provided her with the necessary changes to the stylesheet. 

I replaced the lines in the stylesheet with these ones: 

<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="2.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:strip-space elements="*"/>
    <xsl:output method="html" version="4.0" encoding="UTF-8" indent="yes"/>
    <xsl:template match="/">
        <html>
            <body>
                <h2>
                    <xsl:value-of
                        select="teiCorpus/teiHeader/fileDesc/sourceDesc/biblFull/titleStmt/title"/>
                </h2>
                <h3>Page <xsl:value-of
                    select="teiCorpus/TEI/teiHeader/fileDesc/sourceDesc/bibl/biblScope"/></h3>
                <xsl:for-each select="teiCorpus/TEI/text/body/p">
                    <p><xsl:apply-templates/></p>
                </xsl:for-each>
                <h3>Key:</h3>
                <ul>
                    <li style="color:blue;text-decoration:none;">Individual</li>
                    <li style="color:#00CC00;text-decoration:none;">Location</li>
                    <li style="color:red;text-decoration:none;">Claim</li>
                </ul>
            </body>
        </html>
    </xsl:template>
    <xsl:template match="persName">
        <a style="color:blue;text-decoration:none;" href="{@ref}" title="{@key}&#013;({@from}-{@to})&#013;{@role}"><xsl:value-of select="."/></a>
    </xsl:template>
    <xsl:template match="placeName">
        <a style="color:#00CC00;text-decoration:none;" href="{@ref}" title="{@key}"><xsl:value-of select="."/></a>
    </xsl:template>
    <xsl:template match="interp">
        <a style="color:red;text-decoration:none;" title="{@key}&#013;&#013;{@n}, available at {@ref}"><xsl:value-of select="."/></a>
    </xsl:template>
    
</xsl:stylesheet>

However because I had added an “Organisation” category, after the line 34 I added my own: 

<xsl:template match="orgName">
       <a style="color:red;text-decoration:none;" title="{@key}&#013;&#013;{@n}, available at {@ref}"><xsl:value-of select="."/></a>
   </xsl:template>

I saved my encoded transcribed with .XML and the stylesheet with .XLS and put them in the same folder on my desktop.

I then went to Firefox and dragged and dropped that file. 

I had made a couple formatting errors so I fixed those and was able to then see my file. 

Only the organisations and some of the names had worked, none of the locations. 

I then tried a couple things to solve the problem 

I tried to change the location tab in the stylesheet and made it to this <xsl:template match="placeName">
        <a style="color:green;text-decoration:none;" title="{@key}&#013;&#013;{@n}, available at {@ref}"><xsl:value-of select="."/></a>

(note it was not the same length as the others at first, and this change solves that problem). It did not work. 

I then tried adjusting my Plugin settings on Firefox, that did not work. 

I tried reuploading the file, that did not work. 

I double checked that everyone was encoded properly, and to my eyes it was.  It still did not work. 


I decided to stop here as I was running out of time. 
