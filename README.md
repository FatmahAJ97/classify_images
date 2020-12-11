#!/usr/bin/env python3
# -*- coding: utf-8 -*-
# */AIPND-revision/intropyproject-classify-pet-images/classify_images.py
#                                                                             
# PROGRAMMER:Fatmah Alyammahi
# DATE CREATED:17/11/2020                                
# REVISED DATE: 
# PURPOSE: Create a function classify_images that uses the classifier function 
#          to create the classifier labels and then compares the classifier 
#          labels to the pet image labels. This function inputs:
#            -The Image Folder as image_dir within classify_images and function 
#             and as in_arg.dir for function call within main. 
#            -The results dictionary as results_dic within classify_images 
#             function and results for the functin call within main.
#            -The CNN model architecture as model wihtin classify_images function
#             and in_arg.arch for the function call within main. 
#           This function uses the extend function to add items to the list 
#           that's the 'value' of the results dictionary. You will be adding the
#           classifier label as the item at index 1 of the list and the comparison 
#           of the pet and classifier labels as the item at index 2 of the list.
#
##
# Imports classifier function for using CNN to classify images 
from classifier import classifier 

# TODO 3: Define classify_images function below, specifically replace the None
#       below by the function definition of the classify_images function. 
#       Notice that this function doesn't return anything because the 
#       results_dic dictionary that is passed into the function is a mutable 
#       data type so no return is needed.
def classify_images(images_dir, results_dic, model): 
    #process all files in results_dic
    for key in results_dic:
        
 #  Runs classifier function to classify the images classifier function 
       # inputs: path + filename  and  model, returns class_label 
        class_label=classifier(images_dir+key,model)
 #(USING HINT) TODO: 3b. BELOW REPLACE pass with CODE to process the model_label to 
       #           convert all characters within model_label to lowercase 
       #           letters and then remove whitespace characters from the ends
       #           of class_label. Be certain the resulting processed string 
        class_label=class_label.lower()
        class_label=class_label.strip()
        
      # defines truth as pet image label
        truth = results_dic[key][0]
       # to add the classifier label (class_label) and the value of
       #1 (where the value of 1 indicates a match between pet image 
       #label and the classifier label) to the results_dic dictionary
       #for the key indicated by the variable key 
        if truth in class_label:
            results_dic[key].extend([class_label, 1])
        #following hint instructions
        else:
            results_dic[key].extend([class_label, 0])
   # print(results_dic)   
   
