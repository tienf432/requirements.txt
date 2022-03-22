# requirements.txt
import pytesseract # this is tesseract module
import matplotlib.pyplot as plt
import cv2 # this is opencv module
import streamlit as st 
import os
from PIL import Image

def load_image(image_file):
	img = Image.open(image_file)
	return img

st.subheader("Image")
image_file = st.file_uploader("Upload Images", type=["png","jpg","jpeg"])

if image_file is not None:
  # To See details
  file_details = {"filename":image_file.name, "filetype":image_file.type, "filesize":image_file.size}
  st.write(file_details)

  # To View Uploaded Image
  img = load_image(image_file)
  st.image(load_image(image_file))
  predicted_result = pytesseract.image_to_string(img, lang ='eng')
  st.write(predicted_result)
