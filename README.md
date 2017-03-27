# IGL17Spring
The primary goal of this project is to study traffic patterns in Manhattan and draw traffic behavior insights for urban planning. Our group focuses on applying Dijkstra and Arc-Flags algorithms to identify travel paths with most interesting traffic behaviors. 

Match links with real geographic locations on Manhattan map using linkids. 

Each street (avenue) between the closest two intersections in Manhattan’s geographic map is coded as an unique link id in our datasets and we call it a link. To make analyzing and interpreting traffics easier, we need to easily match one path on map with one link in our datasets. Therefore we created an interactive map by Python folium package using link.csv which contains link ids information for most roads in Manhattan. With the interactive map, we can easily find the link id of a street area by clicking it on map. 

(Screenshot illustration of the interactive map) 

Compare how signatures correlate with each other

We use signatures to describe the traffic patterns in Manhattan.  Each signature is a vector representing the relative traffic amount in a set of links in all 8760 hours of one year. There are 50 basic signatures who are independent of each other and we use them as base vectors. We examined the relationship between any two signatures using Spearman Rank Correlation Coefficient (tho) and found several pairs of highly-associated signatures. Spearman is usually used on reveal the monotonic relationship between two non-normally distributed variables and tho ranges from -1 to 1. When one variable increases and 

(Graphs)

Create an interactive window on which you can enter a signature id to return map pf which links use that signature. 

To better visualize the 


Find hot spots and corresponding link ids on Manhattan map. (Urban planning)

We utilized our knowledge of the unique urban fabric of Manhattan and found “hot spots” that accommodate significant changes in activity at specific times. We used census tracts provided by New York City’s Open Data portal and based our selections off of the character of the neighborhood therein. We used wealth, employment density, and number of attractions (theatres, nightclubs, museums, galleries, etc.) as parameters to find these places. These census tracts are bounded by specific streets, making it easy to analyze like IDs. From there, we collected link IDs from the map for analysis. We selected five census tracts, comprising the heart of four distinct areas of Manhattan (for one we combined two adjacent census tracts to make four shapes in total), they are listed in the table below:



Census Tract Number
Assigned Region, Colloquial Neighborhood Name
Special qualities
Tract 47 & 49
(combined)
Lower Manhattan/SoHo, SoHo
High income, significant retail and cultural activity at galleries.
Tract 73
Upper East Side, Central Park East
High income residential, large concentration of museums.
Tract 99
Union Square/Gramercy Park and Midtown, Chelsea
High income residential, retail, and prevalence of nightlife (clubs, bars), Javits Convention Center
Tract 119
Midtown, Broadway Theater District
High income retail, large concentration of Theater


Extract data corresponding to 2*2 grid from data_travel_times.csv and assign weights to run dijkstra’s algorithm. 

Dijkstra is an algorithm that gives the shortest path between any two nodes in a directed, weighted traffic network. Specifically, “it solves the single-source shortest path program on directed graphs with nonnegative edge weights”. Note that “the single-pair shortest path (SPSP) problem is to find for a given graph G = (V, E, ω) and nodes s and t the distance d(s, t)”.  In our case, we are interested in the path with shortest travel time between two nodes (intersections), thus we assign travel time to the edges (paths connecting any two nodes) instead of travel distance using a large file called data_travel_times.csv. Our function takes a specific hour (a column index in data_travel_times.csv) as the parameter to find the shortest path between each pair of nodes during that time. Note that if there is no data in that entry in data_travel_times.csv, we consider there is no edge between those two nodes (weight of 0 is meaningless). We first applied Dijkstra to a 2X2 grid area close to Time Square.  In the illustration 2X2 block below, for randomly chosen start node A and end node F among the nine intersections, Dijkstra told us that the fastest route (shaded in blue) for one taxi to travel on in a given hour with average time of 227.533.  





Break the nodes to 3 regions and run arc-flags. Compare shortest path given by dijkstra and arc-flags. 

Arc-flags is a modification of Dijkstra which speeds up by saving memory. 

Extend to 10*10 grid. 





Divide Manhattan into different regions to capture traffic behavior. (Urban planning)

Based on the parameters set forth in our selection method, we subdivided the Borough of Manhattan into nine regions based on employment density, cultural and education institutions, population, and income. The regions are as follows, from south to north:
Downtown: South Manhattan, it boasts a high employment density and density of government facilities at City Hall Park, mostly high-end commercial offices. The 9/11 Memorial is a hub for tourists and the WTC, Fulton Street Transit Center, and the Staten Island Ferry Terminal are all transportation hubs.
Lower Manhattan/SoHo: This neighborhood is mostly mid-rise, high income apartments, there is a high density of cultural facilities, namely art galleries, and many luxury retail service. New York University’s student body may also play a role in the neighborhood’s character.
Union Square/Gramercy Park: The neighborhood is high income, has a mix of uses, is slightly denser than SoHo, has tourism hot spot at Union Square and the Flatiron district, and has a robust nightlife scene.
Midtown: The heart of New York, it has transportation hubs at Penn and Grand Central Station, the Broadway Theater District, Times Square, the Empire State Building, many tourist hot spots, and a high employment density. The UN Headquarters may also have an effect on the traffic patterns.
Upper West Side: Mainly a residential and cultural district, high-end housing, museums, and the Lincoln Center for the Performing Arts are what the district consists of.
Upper East Side: Similar to the Upper West Side, but separated by Central Park, high density of museums and housing.
Harlem: High density of cultural facilities, but lower income than the rest of Manhattan. The economic status of the neighborhood may reflect on the taxi ridership patterns.
Morningside/Manhattanville: Middle-income neighborhood but with a high density of academic institutions due to Columbia Univ., Barnard College, and CCNY, the student body and number of academics may affect the traffic patterns.
Far North/Hudson: Very far north edge, many highways passing through, but a low level of income and employment density.




Midterm Presentation

In middle of March, we composed a summary slide with Homology group and presented our results to IGL scholars and faculties. 
