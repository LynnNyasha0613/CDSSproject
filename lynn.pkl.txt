# -*- coding: utf-8 -*-
"""
Spyder Editor

This is a temporary script file.
"""
#import libraries
import streamlit as st
import pickle
import pandas as pd
import numpy


#Import the loaded model
pickle_in = open('lynn.pkl', 'rb')
classifier = pickle.load(pickle_in)

def pred(symptom1,symptom2,symptom3,symptom4):
    '''
    parameters:
		name:  symptom1
		in: query
		type: text
		required: True
        name: symptom2
        in: query
        type: text
        required: True
	responses:
		200:
			description: output values
    
    '''
    prediction=classifier.predict([[symptom1,symptom2,symptom3,symptom4]])
    print(prediction)
    return prediction

def main():
    #Define title
    st.title('Disease Classification')
    #html_temp =
    symptom1=st.text_input("symptom1","Type here", key='Type')
    symptom2=st.text_input("symptom2","Type here")
    symptom3=st.text_input("symptom3","Type here")
    symptom4=st.text_input("symptom4","Type here")
    result = " "
    if st.button("Predict"):
        result=pred(symptom1,symptom2,symptom3,symptom4)
    st.success("output is {}".format(result))
    
    
    


if __name__ == '__main__':
    
    main()
    
