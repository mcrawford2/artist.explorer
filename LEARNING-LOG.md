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

# What was the trickiest part of getting fetch to work?

# If AI helped, what did it explain about async/await?
AI did help, especially with loading the images along with text information. However, my first attempt at fetching the API and AI's first attempt at helping me did not include async or await. I had to go back and ask AI to help with adding them directly, because I know that they make the code with sequential operations easier to read, simplify error handling, and have clearer tracebacks for debugging. 