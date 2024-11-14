Introduction to Shiny

Shiny is a R package developed by RStudio that allows us to create web application that combine R computational features and web development.

A Shiny application must be contained within a file called app.R and is composed of the following components:


library(shiny)

ui <- fluidPage(
  
# UI code goes here  
  
)

server <- function(input, output) {
  
# Server code goes here
  
}

shinyApp(ui = ui, server = server)

Creating a Shiny Application

There are many ways to create a Shiny application but the easiest is to go through RStudio as follows:

    Go to File.
    Select New Project.... A new window pops up.

new directory window in RStudio

    Select New Directory.
    Select Shiny Web Application.

    Now, you’ll have to name the directory that will contain the app.R file and provide the path where this directory will live.

    Finally hit Create Project. RStudio will create a folder called my_first_shiny_app. Within that folder you’ll find the app.R file. In other word, the file that will contain the application.

🖐️ 🖐️ 🖐️

    There is one other way to structure a Shiny application which consists of partitionning the app.R file into two files: ui.R and server.R. You can find more information here

🖐️ 🖐️ 🖐️
Running a Shiny Application

Open the app.R, you should see the following template created for you by RStudio:

# This is a Shiny web application. You can run the application by clicking
# the 'Run App' button above.
#
# Find out more about building applications with Shiny here:
#
#    http://shiny.rstudio.com/
#

library(shiny)

# Define UI for application that draws a histogram
ui <- fluidPage(

    # Application title
    titlePanel("Old Faithful Geyser Data"),

    # Sidebar with a slider input for number of bins 
    sidebarLayout(
        sidebarPanel(
            sliderInput("bins",
                        "Number of bins:",
                        min = 1,
                        max = 50,
                        value = 30)
        ),

        # Show a plot of the generated distribution
        mainPanel(
           plotOutput("distPlot")
        )
    )
)

# Define server logic required to draw a histogram
server <- function(input, output) {

    output$distPlot <- renderPlot({
        # generate bins based on input$bins from ui.R
        x    <- faithful[, 2]
        bins <- seq(min(x), max(x), length.out = input$bins + 1)

        # draw the histogram with the specified number of bins
        hist(x, breaks = bins, col = 'darkgray', border = 'white')
    })
}

# Run the application 
shinyApp(ui = ui, server = server)

To render the application you can either hit the Run App button (top right corner, beside a green triangle) or you can execute the following command in the Console:


shiny::runApp()

Productivity matters, if you want to speed up your Shiny development you might want to use the keyboard shortcut CTRL/Command + Shift + Enter

👕👕👕 Exercise 1 👕👕👕

    Create a new shiny application, run the template app and change the value of the bins. What do you observe ?

👕👕👕👕👕👕👕👕👕👕
