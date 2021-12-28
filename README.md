# New Commands for designing a cover page - DOCUMENTATION
____
Author : Xemota
Date : 12-27-2021
Version : 0.01

____
### Goal of this piece of work
This file contains the result of my research to make the design that I want. I don't pretend to be an expert in latex. In reality I'm kind new to LaTex, I learn it with the goal to use it instead of microsoft word. 
So, these pieces of code are not from me, I put some parts and reorganize them to provide the result that I want. It is certain that these parts of code are not optimized, but that works fine. 
____
### License
Due to the origin of all of code present in this paper (and my philosophy for the open source knowledges), you can :
- use these commands inside yours projects
- modify these commands as you want

I would like to thank the people who contribute to the knowledge sharing via the forums. Thanks to them, I can manipulate what I want on my document and I want to share you this piece of work for free with any restrictions. 
____

### Documentations related to new commands

First of all, these commands require some libraries listed below :
- \usepackage[pscoord]{eso-pic}  
         This library allows to take the zero point of the coordinate systemis (lower left 
         corner of the page) 
- \usepackage[dvipsnames]{xcolor}
        \usepackage[colorlinks=true, allcolors=blue]{hyperref}
        These libraries are used to allow more choice for the font color
- \usepackage{lmodern} 
        Allows to have title with size above the Latex's limits
- \usepackage{graphicx,tikz}
        Allow to take care into account images 
- \usepackage{caption}
        Allow to add caption below your tables 
        
List of commands used inside pages : 
1. \NCDisplayIMAGEbackground{width}{NamePicture.extension}
2. \NCFloatingTEXTbox{posX}{posY}{text}{color}
3. \NCFloatingLINEseparate{posX}{posY}{heigthOFline}{color}
4. \NCFloatingIMAGEbox{posX}{posY}{scale}{image.extension}
5. \NCModularFONTsize{size}
6. \NCFloatingTEXTAREAbox{posX}{posY}{widthBox}{text}
     
Here you can find more details about new commands used inside latex project for the
first cover page. The following lines are structures as suite : 
- Code
- Purpose of the command's function
- Details of parameters 




#### 1. \textbf{NCDisplayIMAGEbackground}
     code :
  	           \newcommand{\NCDisplayIMAGEbackground}[2]{
        				 \AddToShipoutPictureBG*{
             				\AtPageLowerLeft{\includegraphics[width=#1pt,height=\paperheight]{./images/#2}}
                 }
    			     }
      
Purpose of this command's function : allows to display a picture in the background 
of the current page.

This function is used like this : 
\NCDisplayIMAGEbackground{width}{NamePicture.extension}

This function take two parameters. The first one is related to the width of the picture (that
can be above then 1000pt). And de last one is related to repository containing all images
of your project. According to the eextension of your image file, please write name of your 
picture followed by the extension (png, jpeg, jpg, ...).




#### 2. \textbf{NCFloatingTEXTbox}
          code : 
          			\newcommand{\NCFloatingTEXTbox}[4]{ 
                	 \setbox0=\hbox{#3}
         			     \AddToShipoutPictureFG*{
               					 \put(\LenToUnit{#1\paperwidth},\LenToUnit{#2\paperheight}){\vtop{{\null}\color{#4}\makebox[0pt][c]{#3}}}
           				 }
        			  }
        
Purpose of this command's function : allows to display a floating text box where 
you can place anywhere on the current page. 

This function is used like this :
\NCFloatingTEXTbox{posX}{posY}{text}{color}

This function take four parameters. The first and second ones are related to the
location on the current page (X and Y). Take care to write a number between 0 and 1
for these parameters. The third one allows to contain the text under this form : 
\texttt{your text}. You can use the method "NCModularFONTsize" to modify the size
of the font (for more explanation, please to refer to this function below in this file). 
The last one allows to change the font color. Please refer to this website to know what 
kind of color your can use : 
https://fr.overleaf.com/learn/latex/Using_colours_in_LaTeX
      
      
      
      
#### 3. \textbf{NCFloatingLINEseparate}
          code : 
          		   \newcommand{\NCFloatingLINEseparate}[4]{ 
           				 \AddToShipoutPicture*{
               				 \put(\LenToUnit{#1cm},#2cm){\color{#4}\line(0,0){\LenToUnit{#3\paperheight}}}
         		  	 	 } 
        		  	 }
          
Purpose of this command's function : allows to display a vertical floating line where 
you want and anywhere on the current page. 

This function is used like this :
\NCFloatingLINEseparate{posX}{posY}{heigthOFline}{color}

This function take four parameters. The first and second ones are related to the
location on the current page (X and Y). Take care to write a number in centimeter unit
for these parameters. The third one allows to resize the length of the line (it is a 
number in range of 0 to 1). The last one allows to change the font color. Please refer to
this website to know what kind of color your can use : 
https://fr.overleaf.com/learn/latex/Using_colours_in_LaTeX
           
    
  
  
#### 4. \textbf{NCFloatingIMAGEbox}
             code : 
          		    \newcommand{\NCFloatingIMAGEbox}[4]{
           	 			   \AddToShipoutPicture*{
                			   \put(\LenToUnit{#1\paperwidth},\LenToUnit{#2\paperheight}){\includegraphics[scale=#3]{images/#4}}
            			   } 
     			        }
         
Purpose of this command's function : allows to display a floating picture where 
you want and anywhere on the current page. 

This function is used like this :
\NCFloatingLINEseparate{posX}{posY}{scale}{color}

This function take four parameters. The first and second ones are related to the
location on the current page (X and Y). . The third one allows to rescale the size of
the piecture. All of these three parameters are a number between 0 and 1. The last one 
allows to change the font color. Please refer to this website to know what kind of color
your can use : 
https://fr.overleaf.com/learn/latex/Using_colours_in_LaTeX    
    
  
  
  
#### 5. \textbf{NCModularFONTsize} 
          code : 
          		    \newcommand{\NCModularFONTsize}[2]{\fontsize{#1pt}{10pt}\selectfont}
                  
Purpose of this command's function : allows to resize the font size. The main 
specificity of this command is that your can pass over LaTex's limits.  

This function is used like this :
\NCModularFONTsize{size}

This function take one parameters. This parameter is a number. its value is 11 or 12 for 
the normal size. For huge font size, you can put 28 for this parameter.

  
  
  
#### 6. \textbf{NCFloatingTEXTAREAbox}
          code : 
          		    \newcommand{\NCFloatingTEXTAREAbox}[4]{
           				    \AddToShipoutPicture*{
            				    \put(\LenToUnit{#1\paperwidth},\LenToUnit{#2\paperheight}){\parbox[1pt]{#3cm}{#4}}
           				    } 
        			    }
         
 Purpose of this command's function : allows to resize the font size. The main 
 specificity of this command is that your can pass over LaTex's limits.  

 This function is used like this :
 \NCFloatingTEXTAREAbox{posX}{posY}{widthBox}{text}

 This function take four parameters. The first and second ones are related to the
 location on the current page (X and Y). Take care to write a number between 0 and 1
 for these parameters. The third one allows to resize the width of the text. The last one
 allows to contain the text under this form : \texttt{your text}. You can use the method
 "NCModularFONTsize" to modify the size of the font (for more explanation, please to
 refer to this function below in this file).





references : 
https://tex.stackexchange.com/questions/24663/how-to-place-a-floating-text-box-at-a-specified-location-in-page-coordinates



