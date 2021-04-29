## Tetris

---

#### Rotation Logic 

Basically I used SRS Rotation System

> - *When unobstructed, the tetrominoes all rotate purely about a single point. These apparent rotation centers are shown as circles in the diagram.*

`Single Point (Pivot)` is different by box size (ie 2, 3, 4) 

I calculate `O` block as size of 2 (0, 0), (0, 1), (1, 1), (1, 0)

Box size of `I` block is 4  and 3 for all other blocks



#### How to Rotate

Rotate by (0, 0) - (box size / 2, box size / 2)

Use Transformation matrix to rotate ${1 \over 2}\pi$ clockwise rotate ${3\pi\over2}$
$$
Clockwise \ Rotation \
{1 \over 2}\pi
Counter \ Clockwise \ Rotation \
{3 \over 2}\pi \
$$

$$
\begin{align}
Use\ transformation \ matrix\ to\ rotate \ 
{pi \over 2} to \ clock wise \ rotation
{3 \over 2 }\pi \\
Clockwise \ Rotation\ Matrix \ 
\begin{pmatrix}
\cos\theta & \sin\theta \\
-\sin\theta & \cos\theta \\
\end{pmatrix}
\\ \\
Counter\ Clockwise \ rotaion \ Matrix
\begin{pmatrix}
\cos\theta & -\sin\theta \\
\sin\theta & \cos\theta \\
\end{pmatrix}
\end{align}
$$

>And basically coordinates starts positive column and row because of array index
>
>So we align the coordinates to pivot point which different by box size
>
>3 x 3 block' s pivot point is `(1, 1)` 
>
>2 x 2 block' s pivot point is `(0.5, 0.5)` 
>_pivot point align between block_
>
>4 x 4 block's pivot point is `(1,5 1,5)`
>
>First move transformation to pivot point 
>
>And move again to original point

$$
\begin{align}
\begin{pmatrix}
0 & 1 \\
-1 & 0 \\
\end{pmatrix} \
\begin{pmatrix}
x \ - \ c \\
y \ - \ c \\
\end{pmatrix} +
\begin{pmatrix}
c \\
c
\end{pmatrix} \\
\end{align}
\\
\begin{pmatrix}
x \\
y \\
\end{pmatrix} =>
\begin{pmatrix}
y\\
2c\ -x
\end{pmatrix}
$$





> Block will move by direction when direction key hits
>
> So we have to adjust coordinates of blocks
>
> Let's say moved Colum by a and Row by b

$$
\begin{align*}
Column \ moved \ by \ a \\
Row \ moved \ by \ b
\end{align*}
\\
\begin{pmatrix}
0 & 1 \\
-1 & 0 \\
\end{pmatrix} \
\begin{pmatrix}
x \ - \ a- \ c \\
y \ - \ b - \ c \\
\end{pmatrix} +
\begin{pmatrix}
c + a\\
c + b
\end{pmatrix} =
\begin{pmatrix}
y + a - b \\
a + b + 2c - x \\

\end{pmatrix}
$$



#### Implementation

> Block coordinates based x, y plane  starts at 0,0
>
> For example `Z` Block Coordinates $\begin{pmatrix}(1 , 0 ),( 1, 1)\\(2,1),(2,2)\end{pmatrix}$ Pivot point is `0, 0` but it moved 1 to x axis 1 to y axis
>
> And box size is 3
>
> But O, I block' pivot is between the block area I -> (1.5, 1.5) O -> 0.5, 0.5 
>
> _half of 0~3 and half of 0~1_
>
> So we have to adjust pivot point by box size 
>
> Every coordinates of blocks in first quadrant shifted by ${box size-1 \over 2 }$ up and right
>
> Calculate it and we have rotated block by same pivot

> $$
> \begin{align}
> a = 1 \ b = 1 \ c = 3 / 2 - 0.5 \ boxsize  
> 
> \end{align}
> \\
> \begin{pmatrix}
> 0 & 1 \\
> -1 & 0 \\
> \end{pmatrix} \
> \begin{pmatrix}
> x \ - \ 1- \ c \\
> y \ - \ 1 - \ c \\
> \end{pmatrix} +
> \begin{pmatrix}
> c + 1\\
> c + 1
> \end{pmatrix} =
> \begin{pmatrix}
> y + 1 - 1 \\
> 1 + 1 + 2 - x \\
> 
> \end{pmatrix}
> $$