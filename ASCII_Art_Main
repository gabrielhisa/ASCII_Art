# Programming projects for Advanced Beginners: ASCII art
# (https://robertheaton.com/2018/06/12/programming-projects-for-advanced-beginners-ascii-art/)
# This is my first attempt to create a simple program!

from PIL import Image
from colorama import init, Fore, Style
init(convert = True)

# Importing the image and reducing its size to a thumbnail
size = 256,256
image = Image.open('C:/Users/Alexandra Lindona/Desktop/Gaga/Projects/ASCII Images/profilepic.jpg')
image.thumbnail(size)
width, height = image.size

# Creating a list to store the ASCII characters, also in a way to invert brightness
ASCII_chars = "`^\",:;Il!i~+_-?][}{1)(|\\/tfjrxnuvczXYUJCLQ0OZmwqpdbkhao*#MW&8%B@$"
char_list = []
char_list_inverse = []
for char in ASCII_chars:
    char_list.append(char)

char_list_inverse = char_list[::-1]


# Creating a matrix to accomodate the pixel matrix and then scanning the image into the matrix
def get_pixel_matrix():
    px_matrix = [[0 for x in range(width)] for y in range(height)]
    # Returning all the pixel as tuples to this variable
    px = list(image.getdata())
    # Inserting the list of tuples in the matrix
    px = list(image.getdata())
    i = 0
    for x in range(len(px_matrix)):
        for y in range(len(px_matrix[x])):
            px_matrix[x][y] = px[i]
            i += 1
    return px_matrix


# Getting the tuple's means as a value for brightness, and adding them to a new matrix
def get_brightness_matrix(matrix, option=1):
    brightness_matrix = []
    # Average brightness
    if option == 1:
        sum = 0
        for x in range(len(matrix)):
            row = []
            for y in range(len(matrix[x])):
                for element in matrix[x][y]:
                    sum += int(element)
                mean = round(sum/3, 0)
                row.append(int(mean))
                sum = 0
            brightness_matrix.append(row)
        return brightness_matrix
    # MinMax brightness
    if option == 2:
        minimum = maximum = result = 0
        for x in range(len(matrix)):
            row = []
            for y in range(len(matrix[x])):
                for element in matrix[x][y]:
                    if element > maximum:
                        maximum = element
                    else:
                        minimum = element
                result = (minimum + maximum) / 2
                result = round(result, 0)
                row.append(int(result))
                result = 0
            brightness_matrix.append(row)
        return brightness_matrix
    # Luminosity brightness
    if option == 3:
        sum = 0
        for x in matrix:
            row = []
            for y in x:
                sum = (y[0]*0.21) + (y[1]*0.72) + (y[2]*0.07)
                sum = round(sum,0)
                row.append(int(sum))
                sum = 0
            brightness_matrix.append(row)
        return brightness_matrix

# Now we'll use a little bit of math to calculate which character is going to be used
# when we select a number from the brightness matrix. The equation is going to be
# (x / 255) * 65, rounded to the nearest number so we can fit the char perfectly.
def get_char_matrix(brightness_matrix, inverse=False):
    char_matrix = []
    i = 0
    for x in range(len(brightness_matrix)):
        row = []
        for y in range(len(brightness_matrix[x])):
            value = round((brightness_matrix[x][y] / 255) * 65)
            if inverse == True:
                row.append(char_list_inverse[value]*3)
            else:
                row.append(char_list[value]*3)
        char_matrix.append(row)
    return char_matrix

# Printing the matrix
def print_matrix(char_matrix, color=''):
    for x in range(len(char_matrix)):
        for y in range(len(char_matrix[x])):
            print(color + ''.join(map(str, char_matrix[y])))
        print(Style.RESET_ALL)
        return

# Setting up all together
px_matrix = get_pixel_matrix()

# Setting different brightness matrixes
px_matrix_average = get_brightness_matrix(px_matrix)
px_matrix_minmax = get_brightness_matrix(px_matrix,2)
px_matrix_luminous = get_brightness_matrix(px_matrix,3)
matrixes = [px_matrix_average, px_matrix_minmax, px_matrix_luminous]

# Converting the matrixes to char matrixes, adding one on the negative spectrum
for matrix in matrixes:
    char_matrix = get_char_matrix(matrix)
    print_matrix(char_matrix)
    print_matrix(char_matrix, Fore.GREEN)

