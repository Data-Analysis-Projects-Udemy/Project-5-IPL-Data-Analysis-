# Project 5 IPL Data Analysis
### IPL = Indian Premier League


# a.- Análisis en profundidad del rendimiento de David Warner (bateador australiano)



1. [Obtener los datos de DA Warner ](#schema1)

<hr>

<a name="schema1"></a>

# 1. Obtener los datos de DA Warner

Creamos un filtro para obtener solo los datos de  `David Warner`

~~~python
filt=(df['batsman']=='DA Warner')
df_warner=df[filt]
df_warner.head()
~~~
![img](./images/001.png)


<hr>

<a name="schema2"></a>

# 2. Obtener los valores de los bateos
~~~python
df_warner['dismissal_kind'].value_counts()
df_warner['dismissal_kind'].value_counts().plot.pie()
plt.savefig("./images/dimissal.png")
~~~
![img](./images/dimissal.png)


<hr>

<a name="schema3"></a>

# 3. Obtener los valores de los batsman runs para buscar cual es el que más hace
~~~python
df_warner['batsman_runs'].value_counts()
~~~
![img](./images/002.png)

Para calcular cualquier valor de los runs, hacemos una función.
~~~python
def count_runs(df,runs):
    return (len(df_warner[df_warner['batsman_runs']==runs]))*runs
~~~
Obtenemos los valores y dibujamos un `pie`
~~~python
labels = [1,2,3,4,6]
slices = []
for run in labels:
    slices.append(count_runs(df_warner, run))

plt.pie(slices, labels = labels)
plt.savefig("./images/runs.png")  
~~~
![img](./images/runs.png)

Y ahora con porcentajes
~~~python
plt.pie(slices, labels = labels, autopct = '%1.1f%%')
plt.savefig("./images/runs_port.png")
~~~
![img](./images/runs_port.png)

























Datos
https://drive.google.com/drive/u/0/folders/1101-XU7OimDoHsKg5fcrJsv3BlFYnFm3