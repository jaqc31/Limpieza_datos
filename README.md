# Limpieza_datos
Es un proyecto personal para aplicar y explorar nuevos enfoques en el aprendizaje de limpieza de datos  con pandas 
Lo que necesito saber es si hay alguna funcion que me permita reemplazar los valores de la columna 'DEPARTAMENTO_DE_DOMICILIO_DE_LA_IES'
Lo he venido haciendo de la siguiente manera

# Ahora vamos a identificar que valores estan escritos de distintas maneras para uniformar los registros de las variables,
# Para que nos quede una sola forma de registrar cada departamento
# Vamos a comenzar con san andres

cundi=inscritos['DEPARTAMENTO_DE_DOMICILIO_DE_LA_IES'].str.contains('cundi', case=False, regex=True)

# Obtener los registros que cumplen con el criterio
dep_cundi = inscritos.loc[cundi, 'DEPARTAMENTO_DE_DOMICILIO_DE_LA_IES']

# Obtener los valores únicos
valores_unicos_cun = dep_cundi.unique()

valores_unicos_cun

valor_reemplazo='CUNDINAMARCA'

# Crear el diccionario de reemplazos
diccionario_reemplazos = dict(zip(valores_unicos_cun, [valor_reemplazo] * len(valores_unicos_cun)))

inscritos['DEPARTAMENTO_DE_DOMICILIO_DE_LA_IES']=inscritos['DEPARTAMENTO_DE_DOMICILIO_DE_LA_IES'].replace(diccionario_reemplazos,regex=True)
