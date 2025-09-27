# Implementation-of-Logistic-Regression-Model-to-Predict-the-Placement-Status-of-Student

## AIM:
To write a program to implement the the Logistic Regression Model to Predict the Placement Status of Student.

## Equipments Required:
1. Hardware – PCs
2. Anaconda – Python 3.7 Installation / Jupyter notebook

## Algorithm:

```
1.Import the required packages and print the present data.
2.Print the placement data and salary data.
3.Find the null and duplicate values.
4.Using logistic regression find the predicted values of accuracy , confusion matrices.
```

## Program:
```
/*
Program to implement the the Logistic Regression Model to Predict the Placement Status of Student.
Developed by: SANDHIYA SREE
RegisterNumber:  212223220093
```

```
import pandas as pd
data=pd.read_csv("/content/Placement_Data.csv")
data.head()
```

<img width="781" height="140" alt="image" src="https://github.com/user-attachments/assets/1bc3af65-7920-4027-8267-412044e8ed16" />

```
data1=data.copy()
data1=data1.drop(["sl_no","salary"],axis=1)#Removes the specified row or column
data1.head()
```

<img width="759" height="241" alt="image" src="https://github.com/user-attachments/assets/9cac8a84-ed8b-432b-b772-9678d7bfb256" />

```
data1.isnull().sum()
```

<img width="349" height="810" alt="image" src="https://github.com/user-attachments/assets/121e4536-56e6-4d4b-9c9b-78159c1e3ddb" />

```
data1.duplicated().sum()
```

<img width="295" height="46" alt="image" src="https://github.com/user-attachments/assets/ee919978-49d8-4d40-a8c6-80dd160d34e2" />

```
from sklearn.preprocessing import LabelEncoder
le=LabelEncoder()
data1["gender"]=le.fit_transform(data1["gender"])
data1["ssc_b"]=le.fit_transform(data1["ssc_b"])
data1["hsc_b"]=le.fit_transform(data1["hsc_b"])
data1["hsc_s"]=le.fit_transform(data1["hsc_s"])
data1["degree_t"]=le.fit_transform(data1["degree_t"])
data1["workex"]=le.fit_transform(data1["workex"])
data1["specialisation"]=le.fit_transform(data1["specialisation"])
data1["status"]=le.fit_transform(data1["status"])
data1
```

<img width="662" height="299" alt="image" src="https://github.com/user-attachments/assets/03326838-6ae6-423d-85f1-dbdc69ae0b21" />

```
x=data1.iloc[:,:-1]
x
```

<img width="655" height="313" alt="image" src="https://github.com/user-attachments/assets/7db67fa1-912e-43c9-9bf2-e267c0454455" />

```
y=data1["status"]
y
```

<img width="275" height="730" alt="image" src="https://github.com/user-attachments/assets/25b14a70-26c5-4814-8ed3-c4e1ae75b1f3" />

```
from sklearn.model_selection import train_test_split
x_train,x_test,y_train,y_test=train_test_split(x,y,test_size=0.2,random_state=0)
from sklearn.linear_model import LogisticRegression
lr=LogisticRegression(solver="liblinear")# A library for large linear classification
lr.fit(x_train,y_train)
y_pred=lr.predict(x_test)
y_pred
```

<img width="615" height="43" alt="image" src="https://github.com/user-attachments/assets/c38e6c1c-d3bb-4c9f-b2c8-c0e43b991aec" />

```
from sklearn.metrics import accuracy_score
accuracy=accuracy_score(y_test,y_pred)# Accuracy Score = (TP+TN)/
#accuracy_score(y_true,y_prednormalize=False)
accuracy
```

<img width="374" height="50" alt="image" src="https://github.com/user-attachments/assets/7e083e82-db88-40b6-be45-a1c6647b59b8" />

```
from sklearn.metrics import confusion_matrix
confusion = (y_test,y_pred)
confusion
```
<img width="697" height="786" alt="image" src="https://github.com/user-attachments/assets/3cd8c7a8-3f53-46c5-ac7b-3403d3d77278" />

```
from sklearn.metrics import classification_report
classification_report1=classification_report(y_test,y_pred)
print(classification_report1)
```

<img width="661" height="212" alt="image" src="https://github.com/user-attachments/assets/dbe0f37c-0310-4114-95c6-e9eb2f696cec" />


## Result:
Thus the program to implement the the Logistic Regression Model to Predict the Placement Status of Student is written and verified using python programming.
