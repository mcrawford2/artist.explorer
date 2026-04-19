## ITERATION #1:

# What does the API response look like? 
The API response looks like this (with everything unopened):

    API response: 
    Object
    config: {iiif_url: 'https://www.artic.edu/iiif/2', website_url: 'http://www.artic.edu'}
    data: (4) [{…}, {…}, {…}, {…}]
    info: {license_text: 'The `description` field in this response is licens…nation and the Terms and Conditions of artic.edu.', license_links: Array(2), version: '1.14'}
    pagination: {total: 131565, limit: 4, offset: 0, total_pages: 32892, current_page: 1, …}
    [[Prototype]]: Object

config - gives URLs
data - the content, an array of the 4 starting artwork objects collapsed but when expanded gives more info about each one
info - the data license, links to terms of use, and the API version
pagination - how much of the whole dataset is being shown on the page

# What fields did you use? 
I used the fields artist_display, image_id, and title. Artist display gives information about the artists name, nationality, and years alive. Image ID uses the number code (ex. 85285b97-316e-92e4-53bd-07e565d57db0) for the artwork image. Title gives the name of the artwork. These were e starting fields, and I am likely to incorporate more moving forward.

# What was the trickiest part of getting fetch to work?
The hardest part of getting fetch to work was understanding the written syntax. I had a good understanding of it conceptually, and wanted to be able to complete the written code on my own. I had to turn to AI to help because I did not have in depth enough comprehension of what to write, in what order and with what indents or special characters. Looking back at the partially AI code now, I am able to better understand the entire block of script.  

# If AI helped, what did it explain about async/await?
AI did help, especially with loading the images along with text information. However, my first attempt at fetching the API and AI's first attempt at helping me did not include async or await. I had to go back and ask AI to help with adding them directly, because I know that they make the code with sequential operations easier to read, simplify error handling, and have clearer tracebacks for debugging. There are two awaits because it has to wait for the server to respond, and wait for the body to download. 


## ITERATION #2:

# How did you connect user input to API calls? 
I added user input functionality of search and a load more button. The search ability lets users find what they are looking for directly. It connects to te API after users type in the search box, and an addEventListener runs. The results are filtered based on what the user types, and searches are formatted to be case insensitive and ignore extra spaces. If te search is empty, all loaded artworks will be on the page. 

The load more button works by getting the button element from the DOM, and updating text within the button as long as it is nor currently loading and there are more pages to be loaded. It loads a new 8 artworks from the API, through sending a request, checking HTTP success, parsing JSON, and logging the API response.

# What CSS layout did you use for displaying data? 
I used cards to present the artwork and following information on the page. This was a logical decision for me design-wise because cards seem to naturally mirror how physical artwork is displayed in a museum. Each piece gets its own framed, self-contained space. Using a CSS Grid layout allowed me to arrange these cards in a clean 4-column structure, and each card uses padding, a light border, and a border-radius to create separation between data.

# What design decisions did you make?
I wanted to keep the page very simple. Because it is a page for art, I wanted the art to be the main feature and for it not to be overshadowed by any overwhelming animations. One thing I did add was a slight hover animation for the artwork images, for it to be clear what the user was looking at. Hover also adds a layer of interactivity that encourages users to engage with each piece without disrupting the overall layout.


## ITERATION 3:

# What extension did you add? 
There is already some form of pagination through the load more artwork function, but I also added a detailed view extension. This works by allowing users to click on any artwork, and an "Artork details" section will pop up below. It will show a larger version of the image, and have more information including artist, date, origin, medium, dimensions, department, and how it got to the Art Institute. 

# What edge cases did you handle? 
- empty search: empty search will show all loaded artworks
- spamming load more button after having no search results: continues to return "No artworks match your search."
- long searches: are not likely to have any matches, but user can still try and input will stay within the search box
- API rate limit: the Art Institute of Chicago states 60 requests per minute per IP, which is almost impossible to exceed in this app

Additionally, with a total of 131,565 artworks and your current page size of 8, estimated total pages = about 16,446 and estimated maximum Load more clicks = about 16,445.

# What surprised you about working with a real API?
Working with a real API, I expected things to break constantly. However, this API was very reliable. Most of my fetch calls worked, and when something went wrong it was usually do to my own human error. On the other hand, while the functionality of te API was consistent, it did not always return what it said it would. One example of this is when both the Artist and Origin of an art piece was stated as Turkey. 
