######################################################################################
## This is a replication of part 3 of the excellent data wrangling tutorials by 
## Suzan Baert. The source code may be found at 
## https://suzan.rbind.io/categories/tutorial/
##
######################################################################################


#LOAD REQUIRED PACKAGES
library(tidyverse)

glimpse(msleep)

###BASIC ROW FILTERS----
###1.) Filtering rows based on numeric variables.
#Numeric variables can be filtered based on their values. The most common
#operators for this are >, >=, <, =<, ==, and !=

msleep %>% 
  select(name, sleep_total) %>% 
  filter(sleep_total>18)

###2.) Filtering a range of values.
#Technique 1:

msleep %>% 
  select(name, sleep_total) %>% 
  filter(sleep_total >=16, sleep_total <= 18)

#Technique 2:

msleep %>% 
  select(name, sleep_total) %>% 
  filter(between(sleep_total,16, 18))

#Technique 3:
msleep %>% 
  select(name, sleep_total) %>% 
  filter(near(sleep_total, 17, tol = sd(sleep_total)))

###3.Filtering based on exact character variable matches.
#a.
msleep %>% 
  select(order, name, sleep_total) %>% 
  filter(order == "Didelphimorphia")

#b. 
msleep %>% 
  select(order, name, sleep_total) %>% 
  filter(order != "Rodentia")

#c. 
msleep %>% 
  select(order, name, sleep_total) %>% 
  filter(name > "v")

#d. 
msleep %>%                                   #Take msleep dataset, and then...
  select(order, name, sleep_total) %>%       # Select variables of interest
  filter(order %in% c("Didelphimorphia", "Diprotodontia")) # Filter factors of interest

#e.

remove <- c("Rodentia", "Carnivora", "Primates") #Create a character vector containing factors of the variable "order" and assign to object "remove"
msleep %>%                                       # Take msleep dataset, and then...
  select(order, name, sleep_total) %>%           # Select variables of interest
  filter(!order %in% remove)                     # Filter out factors in object "remove" 

###4. Filtering rows based on regex
msleep %>%                                            #Take msleep dataset, and then...
  select(name, sleep_total) %>%                       # Variables of interest
  filter(str_detect(tolower(name), pattern = "mouse"))# Filter variables that match the pattern "mouse" in its name.

###5. Filtering based on multiple conditions.

msleep %>%                                                 #Take msleep dataset, and then....
  select(name, order, sleep_total:bodywt) %>%              # Select variables of interest
  filter(bodywt>100, (sleep_total >15 | order!="Carnivora"))# Filter rows with body weight greater than one hundred
                                                            # sleeps more than 15hours or does not belong to order Carnivora

#Example with xor

msleep %>%                                #Take msleep dataset, and then...
  select(name, bodywt:brainwt) %>%        # Select variables of interest
  filter(xor(bodywt > 100, brainwt > 1))  # Filter based on logical condition

#Example with !

msleep %>%                                       #Take msleep dataset, and then..
  select(name, sleep_total, brainwt, bodywt) %>% # Select variables of interest
  filter(brainwt > 1, !bodywt > 100)             # Filter rows with brainweight greater than 1 and 
                                                 # and body weight not greater than 100
### 6. Filtering out empty rows.

msleep %>%                                   #Take msleep dataset, and then..
  select(name, conservation:sleep_cycle) %>% # Select variables of interest
  filter(!is.na(conservation))               # Filter out rows with NAs in conservation column
