# pruebaprogramacion

actividad 
1 obtener el nombre de todos los usuarios mayores a 20 años de los siguientes paises: españa. francia y turquia, cuantos son hombres y cuantos son mujeres graficar.

import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv("users.csv")

mayores_20 =df[df["edad"]>20]
df_filtrado = df[
    (df['edad'] > 20) &
    (df['pais'].str.lower().isin(mayores_20))
]
  
nombres_usuarios = df_filtrado['nombre'].tolist()
print("Nombres de usuarios mayores de 20 años en España, Francia y Turquía:")
print(nombres_usuarios)

conteo_genero = mayores_20["genero"].value_counts()
conteo_genero.plot(kind='bar', color=['skyblue', 'pink'])
plt.title("Distribucion por genero de usuarios mayores a 20 años")
plt.xlabel("Genero")
plt.ylabel("Cantidad")
plt.xticks(rotation=0)
plt.tight_layout()
plt.show()


2 obtener los usuarios de las edades entre 45 y 60 contar cuantos son mujeres y hombres y graficar

import pandas as pd
import matplotlib.pyplot as plt

df= pd.read_csv("users.csv")

mayores_45y60= df[df["edad"]>=45]
mayores_45y60= df[df["edad"]<=60]

conteo_genero = mayores_45y60["genero"].value_counts()

plt.figure(figsize=(6,6))
plt.pie(conteo_genero, labels=conteo_genero.index, autopct='%1.1f%%', startangle=90)
plt.title("distribucion de genero de usuarios mayores de 45 hasta 60 años")
plt.axis('equal')
plt.show()
