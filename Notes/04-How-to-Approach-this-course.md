> Written with [StackEdit](https://stackedit.io/).

# How to Approach this course

Welcome to the lecture on how to approach this course. In this article, we suggest some guidelines on how to approach this course, depending on your background.

We have designed the course to build incrementally from a jupyter notebook to a fully integrated API, supported by production code of the machine learning model with proper logging, versioning and testing. Section after section, we will transform the code incrementally, so you can follow on and understand the newly added pieces of code, and how we progressively restructure the code in different scripts and folders. If you are not familiar with writing production code, it is essential that you follow the course in the suggested order, and make sure you visit the code scripts ahead of the video lectures.  

#### Data Scientists

If you are familiar with building machine learning models, but haven't yet deployed a model, we recommend that you follow the sections in the suggested order. Pay particular attention to section 5, where we will refresh the knowledge of essential tools like git, and virtual environments. From section 6 onward, make sure you first checkout the git commit number / section that we point you to and read and familiarise with the code first, ahead of jumping on to the lecture. Then watch the videos, where we will explain more about what the key and new pieces of code are. The key knowledge is in the code scripts, so make sure you fully understand what is going on in the scripts.  

#### Software Engineers

If you are familiar with software engineering best practices, and are an avid developer, then you can skip the video lectures in sections 4 to 7. You probably don't need to go over the code incrementally within each section. You may as well feel comfortable with going over the code in the last commit for each section only. Make sure however that you understand well sections 2 and 3, and understand well how to write code using the scikit-learn pipeline and the code base in the scikit-learn API to write your transformers (included in section 4).

#### Data Engineers

Data Engineers have generally quite mixed backgrounds, so it is hard to make a recommendation that will help the majority. If your role in the organisation is to build and maintain the API services that are serving the model, then the sections on creating a REST API, testing, CI/CD, deployment using PaaS, IaaS and Docker will be the most relevant to you. Make sure you understand the code that builds and trains the models first (section 4), so that then you can understand the different bits that are added to deploy via API or other infrastructures. Section 3, where we describe the different types of architectures and building a reproducible data pipeline from the start, will also be very useful for you.

#### Business Leads and Product Owners

For the people whose role is not technical, but rather bringing teams together in order to deploy and fully integrate a machine learning model with the other systems in the organisation, the most relevant sections are the introduction lectures in each section, where we explain what each of the components and steps needed to deploy a model are. You can probably skip all the technical lectures.

That is all for now.

**Enjoy the course!**
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY2ODA5MDUwOF19
-->