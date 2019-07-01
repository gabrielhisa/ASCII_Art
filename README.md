# ASCII_Art

#### Info

This is my first attempt into developing something more complex than a simples math exercise. The idea was taken from Robert Heaton's [Programming Projects for Advanced Begginers](https://robertheaton.com/2018/12/08/programming-projects-for-advanced-beginners/), adapted to my current knowledge of data structures.

The program is very simple:

1. It uses the libraries PIL for manipulating images and colorama to format ASCII characters
2. The code gets an image and resizes it to a thumbnail, then transforms each pixel in a tuple of RGB colors
3. Each tuple is then added into a matrix of tuples, which suffers transformation to adapt to each degree of brightness (average, min/man and luminous)
4. These new values are then converted into ASCII characters, and can even be inverted into a negative image or shown colored
5. The image is then shown as a matrix of ASCII characters

One of the catches in the code is that, to show the negative image, I just inverted the ASCII character orientation (from lighter to darkest). Although this is very simple, I'm proud that I managed to grasp this little trick.
