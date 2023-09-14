import random
import matplotlib.pyplot as plt
import numpy as np

grid = [10, 10]
values = []
radius = 2
iteration = 0
strength = 0.01

for x in range(grid[0]):
  for y in range(grid[1]):
    iteration += 1
    direction = random.randrange(8)
    angle = direction * 45

    vectorPos = radius * [
        round(x + np.cos(angle), 3),
        round(y + np.sin(angle), 3),
    ]

    values.append(vectorPos)

    factor = np.dot(vectorPos, values[iteration - 1])

    vectorPos += factor * strength
    values[iteration - 1] -= factor * strength

    plt.plot(vectorPos[0], vectorPos[1], 'o')

plt.grid()
plt.show()