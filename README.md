# census_practice
codecademy project on manipulating variables in census data

import codecademylib3

# Import pandas with alias
import pandas as pd

# Read in the census dataframe
census = pd.read_csv('census_data.csv', index_col=0)
#print(census.head())
#print(census.dtypes)
census['birth_year'] = census['birth_year'].replace(['missing'], 1967)
#print(census['birth_year'].unique())
census['birth_year'] = census['birth_year'].astype(int)
#print(census.dtypes)
#print(census['birth_year'].mean())

census['higher_tax'] = pd.Categorical(census['higher_tax'], ['strongly disagree', 'disagree', 'neutral', 'agree', 'strongly agree'], ordered=True)
#print(census)

census['higher_tax_code'] = census['higher_tax'].cat.codes
#print(census['higher_tax_code'].median())

census = pd.get_dummies(census, columns=['marital_status'])
print(census.head())

