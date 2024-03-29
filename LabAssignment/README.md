<div align = "center">

### Computer Graphics and Image Processing

------ **📚 Assignment 1 : Bresenham's Line Drawing Algorithm 📚** ------

<hr>
</div>

## Coding Section of This Algorithm

```python
import matplotlib.pyplot as plt
import numpy as np

plt.title("Bresenham Algorithm Presentation")
plt.xlabel("X Axis")
plt.ylabel("Y Axis")

def bres(x1, y1, x2, y2):
    x, y = x1, y1
    dx = abs(x2 - x1)
    dy = abs(y2 - y1)
    gradient = dy / float(dx)

    if gradient > 1:
        dx, dy = dy, dx
        x, y = y, x
        x1, y1 = y1, x1
        x2, y2 = y2, x2

    p = 2 * dy - dx
    
    # Ploting point initialization
    xcoordinates = [x]
    ycoordinates = [y]

    for k in range(2, dx + 2):
        if p > 0:
            y = y + 1 if y < y2 else y - 1
            p = p + 2 * (dy - dx)
        else:
            p = p + 2 * dy

        x = x + 1 if x < x2 else x - 1

        xcoordinates.append(x)
        ycoordinates.append(y)

    # Create a grid of zeros representing the coordinates
    grid = np.zeros((max(ycoordinates) + 1, max(xcoordinates) + 1))

    # Fill the grid with 1s at the coordinates
    for x, y in zip(xcoordinates, ycoordinates):
        grid[y, x] = 1

    # Show the grid as an image with filled squares
    plt.imshow(grid, cmap='gray', origin='lower')
    
    # Add borders to the blocks
    for x, y in zip(xcoordinates, ycoordinates):
        plt.plot([x - 0.5, x + 0.5, x + 0.5, x - 0.5, x - 0.5], [y - 0.5, y - 0.5, y + 0.5, y + 0.5, y - 0.5], color='black')

    plt.show()

def main():
    x1 = int(input("Enter the Starting coordinate of x: "))
    y1 = int(input("Enter the Starting coordinate of y: "))
    x2 = int(input("Enter the end coordinate of x: "))
    y2 = int(input("Enter the end coordinate of y: "))

    bres(x1, y1, x2, y2)

if __name__ == "__main__":
    main()
```
## Asking for input
![AskingForInput](https://github.com/naimur1046/Computer_Graphics_and_Image_Processing/assets/88675051/a5da71fd-0283-40aa-b9ca-210bcf9c7e38)

## Showing output in graph

![TotalInput](https://github.com/naimur1046/Computer_Graphics_and_Image_Processing/assets/88675051/eed077df-a1ad-4174-a5d8-c22fbfda4cc2)


