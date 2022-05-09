---
title: "Exercise 1"
author: "Andi Li"
date: "2022/5/4"
output:
  pdf_document: default
  html_document: default
---
install.packages("tidyverse")
library(tidyverse)

install.packages("tidygraph")
library(tidygraph)

install.packages("igraph")
library(igraph)

install.packages("ggraph")
library(ggraph)

library(readr)

# Loading data
Connections = read_csv('Connections.csv')

Connections %>% head(5)

# Get the count of your contacts by their current employer + total count
count = Connections %>% count(Company, sort=TRUE)
count

Connections %>% 
  count(Company) %>% 
  arrange(-n)

# Create dataframe
Connections$Nodes = paste(Connections$First.Name, substr(Connections$Last.Name,0,3))
Dataframe_graph <- merge(Connections$Nodes, Connections$Nodes, by=NULL)

Connections$last_initial <- substr($`Last Name`, 1, 1)
Connections$label <- paste(Connections$`First Name`, Connections$last_initial)

Nodes_created <- Connections %>% distinct(label)
Nodes <- created %>% rowid_to_column('Main_ID')

Data_D <- Connections
colnames(Data_D) <- paste(colnames(Data_D), "2", sep="")
join <- tidyr::crossing(Connections, Data_D, .name_repair="minimal")

# edges dataframe
edges <- select(edges, node_1, node_2)
edges

edges %>% head(5)

# Fit the model
network_graph <- tbl_graph(nodes=nodes, edges=edges, directed=FALSE)
network

# Network Graph
library("tidygraph")
library("ggraph")

ggraph(network_graph) + geom_edge_link() + geom_node_point() + theme_graph()

