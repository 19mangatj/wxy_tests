# wxy_tests

This is a brief assignment to assit in the hiring process for urban analysts at WXY. Please complete parts A and B below. Please clone this branch and send us back a link to a repo with answers to part one in a markdown file & a notebook that shows your work on part B. 

Please do not spend more than two-three hours on this assignment. We do not want you to go overboard! 

## A. Web Development 

1. Please share a link to a code base for a website you have built or substantively contributed to. If it was a collaboration please provide a clear description of your role. 

### Submission for Part A.1
#### Frontend example
["Reddit Map Github Link (Final Version)"](https://github.com/iDPI-Umass/reddit-map)
["Reddit Map Github Link (Prototype)"](https://github.com/iDPI-Umass/reddit-map/tree/8eaf274a7f961eba1534486811ec544e5c345ab2/src)
As a part of my senior thesis in college, I helped create ["Reddit Map"](https://redditmap.social/). See the ["about page"](https://redditmap.social/about) for more information. 

My role in the project included working with a data scientist to understand the data we were trying to visualize, creating an initial design of the application using Figma, and prototyping the application for user tests using React and d3.js. 

Through the protyping process, I realize that d3.js is not great for rendering large amounts of data. For the deployed version, I worked with a Software Engineer to transfer my design and prototype into Svelte and Canvas. The developer transferred most of the application into Svelte and Canvas while I focused on thesis/paper writing. I jumped into development later to implement a custom search and accordion feature along with a toggle feature that helped view the impacts of the 2023 Reddit Protest on the site in Svelte. Above, I included code for the prototype and for the final version of the Reddit Map. 

#### Backend example
["Backend for boundaries platform"](https://github.com/19mangatj/wxy_code_sample?tab=readme-ov-file)
Due to issues with fork permissions, I wasn't able to share the whole repo. Instead, I created a private repo with the portion of the project I built (backend). See the `README.md` file of the code sample for details.

2. In no more than a few paragraphs, please describe how you would approach developing a website for the scenario described below. Feel free to include simple diagrams of the architecture as helpful.  

    You are working with the NYC Department of City Planning on a neighborhood plan. As part of the process, we are developing a website to solicit community input on what the plan should include. The website must have an interactive map with context layers and a feature that allows community members to add  comments to the map to share ideas for the plan. The comments should not be publicly visible on the site but must be saved along with their location information so that they can later be analyzed. 

### Answers to part A.2
#### Frontend
I would use React to build out the components of the application. While I'm familiar with libraries such as Leaflet to display map data with context layers, I would need to look into Leaflet and similar libraries to see which would best support user annotations. I would be looking for libraries that allow users to add points and polygons to a map and enable the user to add comments related to these markings. I would also use a component library such as Material UI to implement basic components such as pop-ups and form data. 
On the map, the frontend should include a mechanisms that allow the user to toggle between or layer on top of the different context layers. The map should also have two icons that support creating a dot or a polygon on the map. Once the mark has been made, this should trigger a comment box to appear. If needed, this comment box could be designed as a brief form to allow for structured and unstructured data to be collected related to each mark. 
Other important features could be an address box that allows the user to enter an address and display a marker for the address on the map to help them situate their home in the neighborhood. To do this, the frontend will need to use an API that helps display potential addresses as the user is typing.

There could also be a form below the map, specifically for those users who may not be comfortable using a map to give feedback or for those who may have feedback that may not need geographic data tied to it. We could ask the user to enter the names of streets or landmarks along with their feedback to ensure some sort of geographic connection, if necessary.

#### Backend
I would use MongoDB to store data related to the app. I would use Flask to implement the API to help the backend and frontend communicate. Below, I created a diagram of the architecture of this web app based on the basic features presented in the prompt. I did not include the additional features I suggested in the frontend, but will expand on these below the diagram.

![Alt Text](diagram.png)

If we include an address text box on the frontend, the backend may need mechanisms to check whether the given address is within the neighborhood. This will require a GET and POST API call that verifies the address and stores it if it is within the neighborhood, or sends a message to the frontend if not. On the backend side, this API call could also work on converting the string address to a lat/long point using a geocoding API. An additional POST API call will be needed if there's a form below the map to store any data submitted. These two API calls will require two additional collections in the MongoDB database to store the addresses and form data.

## B. Geospatial Python Test

Please analyze and visualize Active Major Construction permits in New York City in a jupyter notebook (New Building or Major Alteration A1). The data can be downloaded [here](https://data.cityofnewyork.us/Housing-Development/DOB-Permit-Issuance/ipu4-2q9a).

At a minimum:

- Load and clean the data, demonstrate you have a grasp of the data and its contents
- Create a summary table with key metrics
- Visually explore key metrics through graphs 
- Perform a spatial join against another layer of your choice (e.g. Census layers, transit walksheds, etc.)
- Create a summary table making use of the joined data points
- Export one graph and one chart that are presentation-ready or could be slightly refined in Adobe CC 
- Export your final data to excel and shapefile

The objective of this question is to get a flavor for your coding style and analytical approach. We will run the notebook, so make sure you don't have any bugs!

None of your code will be used by WXY for project work.

### Note about Part B
Please see `data_analysis.ipynb` for the notebook with the code. Running the code will require you to have an `output_data/` folder and a `output_data/shapes/` folder which are already in the Github. You will also need `DOB_Permit_Issuance_20250508.csv` and `Historic_Districts_20250508.csv` (from [this link](https://data.cityofnewyork.us/Housing-Development/Historic-Districts-Map-/xbvj-gfnw)). I put `Historic_Districts_20250508.csv` in the `input_data/` folder. `DOB_Permit_Issuance_20250508.csv` is too big to upload on Github after compressing and I didn't get a chance to split up the file so I will share it with you over email or Drive. Alternatively, you can download the data and just change the name of the file in the notebook. I set up a conda virual environment to run the code. The required libraries are in `requirements.txt`.

