## Iteration Generation II
Using a recursive or iterative logic, create a drawing that repeats a simple form into a generative pattern. Drawing inspiration from early computer artists like Molnar and Nake, create a program that applies a particular transformation iteratively. Use this program to generate an SVG file that you will render using a pen plotter.

The following example logic may be helpful as you determine how to create your project:

- First, create the basis for your pattern as a single instance. Try to constrain this drawing to around 100px by 100px. It will be useful to use translation so that you can draw your shape around the point 0,0. 
- Repeat your shapes using a for loop on the x axis
- Create a two dimensional for loop, repeating your shapes down the Y axis as well.
- Once you have a repeating pattern that fills the entire canvas, experiment with ways of shifting the color, style or transformation of the shapes as they advance down the Y axis
- Experiment with ways of incorporating mouse input to manipulate an aspect of the drawing (color, size of certain elements, transformations, etc).
- revise your sketch for a pen plotter using the [svg library](https://github.com/golanlevin/p5.plotSvg). Start with scaling your sketch to 576px by 384 px. This is roughly the equivalent to a postcard (6" by 4"). It will fit neatly into an 8.5" x 11" piece of letter paper.
- if you wish to set up your own computer to use the plotter, [refer to this guide](iDraw_Setup_Guide.html), otherwise use one of the iMacs in Room 325 to print your design. 
- post your sketches to folders named Week 4.1 and Week 4.2. 
- You will have the opportunity to revise your print further over the following week before insatlling the work with your peers.