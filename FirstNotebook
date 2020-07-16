import numpy as np               # A library for all numerical caclulations
import matplotlib.pyplot as plt  # for plotting
import pickle                    # for extracting stored variables

print('I just ran my first Jupyter notebook cell!')

myname="Clare"

print("my name is ",myname)

# load data:
# ----------
# load the PDI data from a pickle file to variables
with open('./introduction_python_variables.pickle', 'rb') as file:
        d = pickle.load(file)
        # print information about each extracted variable:
        for key in list(d.keys()):
            print("extracting pickled variable: name=", key, "; type=",type(d[key]), "; size=", d[key].shape)
        globals().update(d)

print("The dimensions of the input temperature data are:",T.shape)
# note that T is an array with two columns, one for years and one for temperature

# print data for a few years using a for loop:
print("\n year  , Temperature")
for i in range(0,10):
    print(T[i,0],",",T[i,1])
# note that the for loop is indicated by the indentation 
# block, in the above case only a single line is in the loop.

# as another example of a for loop, calculate the mean tempearature using a for loop:
N=len(T[:,0])
Tavg=0
for i in range(0,N):
    Tavg=Tavg+T[i,1]

Tavg=Tavg/N

print("\naveraged temperature is",Tavg)
# note that the average is basically zero, as the temperature record is an anomaly from the mean.

# calculate the mean using a numpy function:
Tavg_numpy=np.mean(T[:,1])
print("averaged temperature calculated by numpy function is",Tavg_numpy)

# code here:
summ = 0
Number = 2020
for i in range (0, Number+1):
    summ += i
    
print("The sum of numbers 1 to 2020 is:")
print(summ)

# plot it:
# --------
fig1= plt.figure(1)
# python array indices are in square brackets and start from zero:
plt.plot(T[:,0],T[:,1])
plt.xlabel("Year")
plt.ylabel("Temperature (C)")
plt.title("observed Temperature record");

# code here:

x = np.arange(-np.pi, np.pi, 0.1)
fig2=plt.figure(2)
plt.plot (x, np.sin(x))
plt.xlabel("x")
plt.ylabel("sin x")
plt.title("sine function")

# find the warmest year using a combination of a loop and an if statement:
Tmax=-100
year_max=-100
# note the indentations denoting the blocks of the for loop and if statement:
for i in range(0,N):  # for loop starts here
    if T[i,1]>Tmax:   # if statement starts here
        Tmax=T[i,1]
        year_max=T[i,0] # this is the last line of both the for loop and the if statement

# note how the last element of the array may be referred to via a -1 index:
print("The first and last years are",T[0,0],T[-1,0])
print("The maximum temperature is", Tmax,", and it occured in year",year_max)

# calculate root mean square:
N=len(T[:,1])
myrms=0.0
for i in range(0,N):
    myrms=myrms+ (T[i,1]**2)
myrms=np.sqrt(myrms/N)

if myrms > ((T [-1,1])-(T [0,1])):
    print ("The rms is larger than the difference")
else:
    print ("The rms is smaller than the difference")
    
# remove mean from each time series:
X=T[:,1]-np.mean(T[:,1]) # x is equal to all the temperatures minus the mean of all the temperatures
Y=CO2[:,1]-np.mean(CO2[:,1]) # y=all the CO2 data minus the average of all the CO2

#will test how close the relationship is
R=np.corrcoef(X,Y)

print("correlation calculated by np.corrcoef is:\n",R)

fig, ax1 = plt.subplots()

color = 'tab:red'
ax1.set_xlabel('year')
ax1.set_ylabel('CO$_2$', color=color)
ax1.plot(CO2[:,0], CO2[:,1], color=color)
ax1.tick_params(axis='y', labelcolor=color)

ax2 = ax1.twinx()  # instantiate a second axes that shares the same x-axis
color = 'tab:blue'
ax2.set_ylabel('Temperature', color=color)  # we already handled the x-label with ax1
ax2.plot(T[:,0],T[:,1], color=color)
ax2.tick_params(axis='y', labelcolor=color)

fig.tight_layout()  # otherwise the right y-label is slightly clipped
plt.show()

# here is how one defines a function:
def my_calc_correlation(X,Y):
    A=0
    B=0
    C=0
    for i in range(0,len(X)):
        A=A+X[i]*Y[i]
        B=B+X[i]*X[i]
        C=C+Y[i]*Y[i]
    R=A/(np.sqrt(B)*np.sqrt(C))
    return R

# and now we can use this function as follows 
# (we use the fact that the mean has been renoved from X,Y)
my_R=my_calc_correlation(X,Y)
print("correlation calculated by my function is:\n",my_R)

letter_list = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
number_list = [0,1,2,3,4,5,6,7,8,9]


my_dictionary = {}
my_dictionary["Letters"]=letter_list
my_dictionary["Numbers"]=number_list

print("keys in dictionary are:",my_dictionary.keys())
print("the first few elements of the first data set are:",my_dictionary["Letters"][4:7])

summ=0
for i in range(2,8):
    summ += my_dictionary["Numbers"][i]

print("The sum of the 3rd-8th elements in the numbers list is:",summ)

