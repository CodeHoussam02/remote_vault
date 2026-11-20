
### 01. Installation process

1. create a virtual env for our stramlit app

```bash
python -m venv .venv
```

2. activate the virtual environment 

```bash
.\.venv\Scripts\activate
```

3. install all your dependencies 

```bash 
pip install stramlit
```

4. create the requirements file 

```bash
touch requirements.txt
```

- after creating this file we need to define the libraries version used in the project 

```python
streamlit==1.42.2
seaborn==0.13.2
matplotlip==3.10.0
pandas==2.2.3
numpy==2.2.1
```

1. In order to run your server you simply type 

```bash 
stramlit run script.py
```

### 02. Familiarize with streamlit library : 

- create a simple heading in your stramlit app 

```python 
import streamlit as st

st.header('Learn stramlit');
```

- write a simple paragraph 

```python
size = 12
st.write('The Box size is : ', size)
```


- simple select box 

```python
shape = st.selectbox('Please enter a shape :', ['Circle', 'Rectangle', 'Square'])
```

- buttons in streamlit 

```python
compute_btn = st.button('Calculate the area')

```

### 03. Sidebar 

- in order to add a sidebar into your application you can do it simply by adding these lines 

```python
st.sidebar.title('Configuration')
```

- write someting inside your sidebar 

```python
with st.sidebar: 
	# all your components here 
	st.selectbox('Please enter something', ['one', 'two'])
```

- ajouter un spinner pour les donnees avant de les calculer 

```python
with st.spinner('Computing ...'):
	st.write('Area : ', area)
	st.write('Perimertre : ', perimetre)
```

### 04. File upload in streamlit

- in order to upload a file (dataset, csv, ...) we need to use the `st.file_uploader()`

```python
st.file_uplader('Upload your file ...', type=['csv'])
```

- how to read csv data and create a simple dataframe from it 

```python
df = pd.red_csv('', encoding="ISO-8859-1")
```

- display the dataframe in a simple table 

```python
st.write(df)
```

- implement a slider to control the number of rows in your table 

```python
num = st.slider('Choose number of rows ', min_value=1, max_value=50, value=10)
st.write(df.head(num))
```

- control the columns that will be shown to the user 

```python
names = st.multiselect('Select columns that you want', df.columns, default=df.columns)
st.write(df.loc[:,names].head(num))
```


### 05. Simple plots on streamlit 

- in this chapter we gonna learn how to plot data using anny visualisation library ou there or using built in graphes in streamlit 
- first of all leat's learn how to plot a `scatter plot` using plotly

```python
import plotly.express as px

# plot a scatter plot
fig_scatter = px.scatter(df, x='Track', y='Spotify Streams')
st.plotly_chart(fig_scatter)

```


### 06. To add to the presentation :

- how to save graphes as ( any extiention ) after creating the graphes.