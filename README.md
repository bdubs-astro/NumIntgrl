# Numerical Integration

Performs numerical integration on x-y data. Uses __Simpson's Rule__ where applicable, and the __Trapezoidal Rule__ in all other cases. 

Returns the **result**, as well as a string indicating the **method** used.

```
    [method, result] = NumIntgrl(x, y);
```

## Methods

### Simpson's 1/3 Rule:

Approximates a function using __2nd order polynomials__.

For ___n___ equal segments (_i.e._, ___n+1___ evenly spaced data points), the definite integral can be approximated as follows. Note that ___n___ must be __even__.

<img src = "./files for README/one third rule equation.png" width = "600"/>

Here ```(b-a)/n``` is the spacing between data points.

<img src = "./files for README/one third rule graphic.png" width = "400"/>

<br>
<br>

<!-- insert page break -->
<div style="page-break-after: always;"></div>

### Simpson's 3/8 Rule:

Approximates a function using __3rd order polynomials__.

For ___n___ equal segments (_i.e._, ___n+1___ evenly spaced data points), the definite integral can be approximated as follows. Note that ___n___ must be __an integer multiple of 3__.

<img src = "./files for README/three eigths rule equation.png" width = "700"/>

Here ```(b-a)/n``` is the spacing between data points.

<img src = "./files for README/three eigths rule graphic.png" width = "400"/>

<br>
<br>

<!-- insert page break -->
<div style="page-break-after: always;"></div>

### Trapezoidal Rule:

Approximates a function using __trapezoids__.

For ___n___ equal segments (_i.e._, ___n+1___ evenly spaced data points), the definite integral can be approximated as follows. 

<img src = "./files for README/trapezoid rule equation v3.png" width = "400"/>

Here ```(b-a)/n``` is the spacing between data points.

<img src = "./files for README/trapezoid rule graphic.png" width = "400"/>

<br>
<br>

<!-- insert page break -->
<div style="page-break-after: always;"></div>

### Test code:

<img src = "./files for README/sine_integral.png" width = "200"/>

```
for Npts = logspace(1, 4, 4) + 1
    x = pi*linspace(0, 1, Npts);
    y = sin(x);
    [method, result] = NumIntgrl(x, y);
    fprintf('n = %-6d \tTrapz = %.6f \t%s = %.6f\n', Npts-1, trapz(x, y), method, result)
end

n = 10     	Trapz = 1.983524 	Simp 1/3 = 2.000110
n = 100    	Trapz = 1.999836 	Simp 1/3 = 2.000000
n = 1000   	Trapz = 1.999998 	Simp 1/3 = 2.000000
n = 10000  	Trapz = 2.000000 	Simp 1/3 = 2.000000
```
```
for Npts = logspace(1, 4, 4)
    x = pi*linspace(0, 1, Npts);
    y = sin(x);
    [method, result] = NumIntgrl(x, y);
    fprintf('n = %-6d \tTrapz = %.6f \t%s = %.6f\n', Npts-1, trapz(x, y), method, result)
end

n = 9      	Trapz = 1.979651 	Simp 3/8 = 2.000382
n = 99     	Trapz = 1.999832 	Simp 3/8 = 2.000000
n = 999    	Trapz = 1.999998 	Simp 3/8 = 2.000000
n = 9999   	Trapz = 2.000000 	Simp 3/8 = 2.000000
```
```
for Npts = logspace(1, 4, 4) + 2
    x = pi*linspace(0, 1, Npts);
    y = sin(x);
    [method, result] = NumIntgrl(x, y);
    fprintf('n = %-6d \tTrapz = %.6f \t%s = %.6f\n', Npts-1, trapz(x, y), method, result)
end

n = 11     	Trapz = 1.986387 	Trap     = 1.986387
n = 101    	Trapz = 1.999839 	Trap     = 1.999839
n = 1001   	Trapz = 1.999998 	Trap     = 1.999998
n = 10001  	Trapz = 2.000000 	Trap     = 2.000000
```

### Resources:

https://web.engr.oregonstate.edu/~webbky/MAE4020_5020_files/Section%208%20Integration.pdf
