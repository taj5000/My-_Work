# <Center> D2 (Declarative Diagram) </Center>

Table of contents:
- Overview
- Installation.
- Shapes
- Connections
- Containers
- Special objects

   . Text & Code

   . Icon & Images

   . SQL Tables

   . UML Classes


## <Center> Overview  </Center>

D2 is a diagram scripting language that turns text to diagram. It stands for declarative diagramming. Declarative means it describe what we want to diagrammed it generates the image.

### **<Center>Features of D2 </centre>**

1. Easy to use.
2. Supports wide variety of formats like PPT and GIF.
3. Provide better readability.

For example, here's two ways to define a cylinder.

**D2:**

```
A: Christmas {shape: cylinder}
```
**Mermaid**

```
A[(Christmas)]
```
D2's is a little less compact but a lot more readable.

## <center> Installation </center>

For linux I have used the below command:

```
curl -fsSL https://d2lang.com/install.sh | sh -s --
```
- This command is a tool for transferring data with URLs. 

- In this context **curl** being used to download the contents of a file from the specified URL.












Here is some practice diagrams which is given below:

  x->y:hello world



This declares a connection between two shapes , x and y, with the label hello world. 



 Connections:
There are 4 valid way to define a connections:

<-> 
->
<-
- -

Example 2.1:
Write replica Canada<-> Write replica Australia




This declares the bi-directional relationship between two shapes, replica Canada and Replica Australia.





Example 2.2:
Read Replica <- Master



Example 2.3:
Lucknow - - Prayagraj


This declares the relationship between two shapes without any direction.



Example 2.4:

super long shape id here --\
 -> super long shape id even longer here



-\  (Here, I am using this symbol to break the syntax line size without impacting the image).


-----------------------------------------------------------------------







3.Repeated Connections:

Repeated connections do not override existing connections. They declare new ones:

Database -> S3: backup
Database -> S3
Database -> S3: backup














4.Cycles:

Step One -> Step Two -> Step Three -> Step Four
Step Four -> Step One: repeat



This declares the repetition of the process.

----------------------------------------------------------------------








5.Arrowheads:
To override the default arrowhead shape or give a label next to arrowheads, define a special shape on connections named .

a: United we stand,divided we fall
b: To thine own self,be true
c: Learn as if you will live forever, live like you will die tomorrow.
a -> b: To err is human, to moo bovine {
 source-arrowhead: 1
 target-arrowhead: * {
   shape: diamond
 }
}


b <-> c: If you can't handle stress you can't handle success  {
 source-arrowhead.label: 1
 target-arrowhead: * {
   shape: diamond
   style.filled: true
 }
}


d: Where there's a will there's a way


d -> a -> c



--------------------------------------------------------------------









6. Reference connections:
Reference a connection by specifying the original ID followed by its index.

x -> y: hi
x -> y: hello


(x -> y)[0].style.stroke: green
(x -> y)[1].style.stroke: yellow

           




7. Containers:

server
# Declares a shape inside of another shape
server.process


# Can declare the container and child in same line
im a parent.im a child


# Since connections can also declare keys, this works too
apartment.Bedroom.Bathroom -> office.Spare Room.Bathroom: Portal




                
—-------------------------------------------------


8.Text:

Text in markdown

Example:
explanation: |md
 # I can do headers
 - lists
 - lists


 etc......

              







If I add two ## or three ### ,the header size will change:

explanation: |md
 ## I can do headers
 - lists
 - lists


 etc......

                    
















explanation: |md
 #### I can do headers
 - lists
 - lists


 etc......

                    


—---------------------------------------------------------------------------------------











9. Latex:

Latex or tex to specify a Latex language block.

plankton -> formula: will steal
formula: {
 equation: |latex
   \\lim_{h \\rightarrow 0 } \\frac{f(x+h)-f(x)}{h}
 |
}

                          
