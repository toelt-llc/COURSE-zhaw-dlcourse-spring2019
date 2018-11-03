Hallo Everyone,
ok I could not resist and I played a bit more with the digits. In the class Afke got a great 62%. With some tweaking I got 72%. I actually first increased the contrast of the images simply converting all pixels with gray values greater than 230 into black pixels, and all the other into white. Additionally instead of converting the 2D images row by row, I converted in a one-dimensional vector column by column with the following code

```
Xinput_rev = np.ndarray(Xinput.shape)
for i in range(Xinput.shape[0]):
    tmp = Xinput[i,:].reshape(28,28)
    Xinput_rev[i,:] = 255*(np.ravel(tmp, order='F') > 230)
```

And then I defined the ratio of the sum of all pixels from 0 to 400 and the ones from 401 to 784 with the lines

```
left = np.sum(Xinput_rev[:,0:400], axis = 1)
right = np.sum(Xinput_rev[:,400:784], axis = 1)
ratio = np.divide(right, left)
```

Not perfect but we have some discrimination. 
In this way we can get 72% of accuracy.

The code can be found now in the repository in the file "Week 2 - Data Analysis Example-3 and 8".
