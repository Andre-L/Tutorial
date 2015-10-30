# Tutorial

import math
import numpy as np
import matplotlib.pyplot as ptl

ert=[]
era=[]

def f(x):
    fun=(math.exp(-x))-x
    return fun
print "Metodo de Bisección"
print ""
print "|%-7s|%-15s|%-15s|%-15s|%-11s|%-11s|"%("i","Xl","Xu","Xr","ErrA","ErrT")
print "|%-7s|%-15s|%-15s|%-15s|%-11s|%-11s|"%("-------","---------------","---------------","---------------","-----------","-----------")

def met_bis():
    global ert
    global era
    xl=float(0)
    xu=float(1)
    i=0
    real=0.56714329
    xr=0
    xR=0
    erra=float(100)
    while(erra>0.000003):
        xr=(xl+xu)/(2)
        
        errt=abs((real-xr)/(real))*100
        ert.append(errt)
        
        erra=abs((xr-xR)/(xr))*100
        era.append(erra)
        print "|%-6d |%-14f |%-14f |%-14f |%-10f |%-11f|"%(i,xl,xu,xr,erra,errt)
        if((f(xl)*f(xr))<0):
            xu=xr
        elif((f(xl)*f(xr))>0):
            xl=xr
        elif((f(xl)*f(xr))==0):
            break
        xR=xr
        i+=1
        
def graficar():
    global era
    global ert
    ptl.plot(ert,color='r',linestyle="--",label="ErrT Met Biseccion")
    ptl.legend(loc="upper right")
    ptl.title("Error Relativo", fontsize = 20)
    ptl.show()
    
    ptl.plot(era,color='b',linestyle="-",label="ErrA Met Biseccion")
    ptl.legend(loc="upper right")
    ptl.title("Error Aproximado", fontsize = 20)
    ptl.show()
    

met_bis()
graficar()
