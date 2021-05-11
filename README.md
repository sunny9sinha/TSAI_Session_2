# TSAI_Session_2
Assignment of TSAI_Session_2 for END2 program

Neural net created in Excel sheet with Learning Rate = 0.5

![alt text](https://github.com/sunny9sinha/TSAI_Session_2/blob/main/Screenshots/LR_05_Scr_1.png)
![alt_test](https://github.com/sunny9sinha/TSAI_Session_2/blob/main/Screenshots/LR_05_Scr_2.png)

Major Steps:
  - Design the neural network as shown in above screenshot, with the given inputs, targets and initial weights.
  - Next major step is to calculate the h1,h2, and the activated h1 and h2 that is nothing but sigmoid of h1 and h2 respectively as we are using activation function as Sigmoid.
  - similarly we calulate o1,o2 and the coressponding activated values.
  - Now the next step is to understand that total Error is the combination of two components coming from two branches and is denoted by E1 and E2.
  - This E1 and E2 is the Mean square error, that is calulated as the square of the difference between expected output and actual output along the two branches. Here 1/2 is included just for simplicity of calulation while taking derivatives.
  - Now with backpropagation we move in backward direction, calculating the rate of change in total error with respect individual weights keeping other weights as constant.
  - We first calculate δE_t/δw5, here we see that w5 has impact only along the path E1 and by using chain rule we can rewrite the equation as : (δE1/δa_o1)*(δa_o1/δo1)*(δo1/δw5)
  - We then calculate each of the components of this equation separately. 
  - And finally we combine the parts together to get : δE_t/δw5 = (a_o1-t1)*(a_o1*(1-ao1))*a_h1
  - And carefully observing the paths for each of the following weights we can rewrite equation for them as :
        δE_t/δw6 = (a_o1-t1)*(a_o1*(1-ao1))*a_h2
        δE_t/δw7 = (a_o2-t2)*(a_o2*(1-ao2))*a_h1
        δE_t/δw8 = (a_o2-t2)*(a_o2*(1-ao2))*a_h2
  - Now moving further in backpropagation , we see the requirement to calculate similar rate of change of total error with respect to other weights.
  - For this we have to get δE_t/δw1 , before calculating it directly we need to get equation for δE_t/δa_h1
  - This a_h1 will have impact along both the paths, ie along the weight w5 and w7, so the impact of a_h1 is distributed along E1 and E2.
  - For calculating δE_t/δa_h1 , we have to combine the equation for δE1/δa_h1 and δE2/δa_h1
  - From the chain rule we can rewrite the equation as δE1/δa_h1 = (δE1/δa_o1)*(δa_o1/δo1)*(δo1/δa_h1)
  - Above one on simplification gives (a_o1 - t1)*(a_o1*(1-a_o1))*w5
  - From the chain rule we can rewrite the equation as δE2/δa_h1 = (δE2/δa_o2)*(δa_o2/δo2)*(δo2/a_h1)
  - Above one on simplification gives (a_o2-t2)*(a_o2*(1-a_o2))*w7
  - So, we get δE_t/δa_h1  = ((a_o1 - t1)*(a_o1*(1-a_o1))*w5) + ((a_o2-t2)*(a_o2*(1-a_o2))*w7)
  - Now to calculate δE_t/δw1 we can again use the chain rule and rewrite equation as δE_t/δw1 = (δE_t/δa_o1)*(δa_o1/δo1)*(δo1/δa_h1)*(δa_h1/δh1)*(δh1/δw1)
  - If we see carefully then the combination of first three components on RHS is nothing but δE_t/δa_h1, so we can rewrite the equation as :
         δE_t/δw1 = (δE_t/δa_h1)*(δa_h1/δh1)*(δh1/δw1) =  (δE_t/δa_h1)*(a_h1*(1-a_h1))*(i1)  , or by putting above calculated value for δE_t/δa_h1 in equation we get
         δE_t/δw1 =( ((a_o1 - t1)*(a_o1*(1-a_o1))*w5)+((a_o2-t2)*(a_o2*(1-a_o2))*w7)*(a_h1*(1-a_h1))*(i1)
  - 

