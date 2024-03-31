# 3001python
#Add input validation : student and test number can't be exceed 11, exam score input range should be 0 to 100
#Calculate the average exams score of the all students
#(extra point) Make it as streamlit web application
#(extra point) deploy your application to the github and stream,io(leave your app address with'#' at the top of the program)

#http://localhost:8501/

import streamlit as st
st.title('average score calculator')
num_student=int(st.number_input('How many students do you have?: '))
num_test_scores=int(st.number_input('How many quiz are you run per student?: '))
if st.button('Submit'):
    #Get the number of students
    while num_student<=0 or num_student>11:
        st.write('number of student must be positive and less than 12')
        num_student=int(st.number_input('How many students do you have?: '))
    #Get the number of test scores per students
    while num_test_scores<=0 or num_test_scores>11:
        st.write('number of student scores must be positive and less than 12')
        num_test_scores=int(st.number_input('How many quiz are you run per student?: '))
    #Determine each student's average test score
    total_score=0.0
    for student in range(num_student):
        total=0.0
        #Initialize an accumluator for test score
        st.write('Student number', student+1)
        st.write('-------------------------')
        for test_num in range(num_test_scores):
            st.write('Test number', test_num+1, end='')
            score=float(st.number_input(': '))
            total=total+score #the same meaning with: total+=score
        #calculate the average test score for this student
        average=total/num_test_scores
        # display the average
        st.write('The average for student number',student+1, 'is',average)
        total_score=total_score+total
        average_total_average=total_score/num_student
    st.write('average for all student: ', average_total_average)
else:
    st.write('please enter information.')
