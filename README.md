# Learning Shiny (My Notes)
## 1st app

Shiny is composed by three elements. <br />
1.UI 2.Server 3.Running Application 
```
library(shiny)

# Define UI for application that draws a histogram
ui <- fluidPage(theme = shinytheme("cerulean"),
                navbarPage("My first app",
                    tabPanel("Navbar 1",
                             sidebarPanel(
                                 tags$h3("Input:"),
                                 textInput("txt1", "Given Name:", ""),
                                 textInput("txt2", "Surname:", ""),
                                 
                             ), # sidebarPanel
                             mainPanel(
                                 h1("Header 1"),
                                 
                                 h4("Output 1"),
                                 verbatimTextOutput("txtout"),
                                 
                             ) # mainPanel
                             
                    ), # Navbar 1, tabPanel
                    tabPanel("Navbar 2", "This panel is intentionally left blank"),
                    tabPanel("Navbar 3", "This panel is intentionally left blank")
                    
                ) # navbarPage
) # fluidPage

```
<img width="943" alt="ShinyR" src="https://user-images.githubusercontent.com/90762709/139598302-b6fd2a5e-6853-4fb4-b0fe-21fa1d2defe9.png">
```
server <- function(input, output) {
    
    output$txtout <- renderText({
        paste( input$txt1, input$txt2, sep = " " )
    })
}
```
On this part we see the output part which prints the text with renderText and takes the ID txtout indicated before on the main menu. As an input it gets 
two input texts IDs and with **paste(input$txt1, input$txt2, sep=' ')** prints the output. <br />
```
# Run the application 
shinyApp(ui = ui, server = server)
```
This part is simply declares the ui and server of the app
