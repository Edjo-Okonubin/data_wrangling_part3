######################################################################################
## This is a replication of part 3 of the excellent data wrangling tutorials by 
## Suzan Baert. The source code may be found at 
## https://suzan.rbind.io/categories/tutorial/
##
######################################################################################

###LOAD REQUIRED PACKAGES
library(tidyverse)
library(stringr)

###FILTERING ACROSS MULTIPLE COLUMNS----
#1.a) filter_all: String

msleep %>%                                       #Take msleep dataset, and then
  select(name:order, sleep_total, -vore) %>%     # Select variables of interest
  filter_all(any_vars(str_detect(., pattern = "Ca"))) #Filter all rows in selected variables that match pattern "Ca"

#1.b) filter_all: Numeric
msleep %>%                              # Take msleep dataset, and then...
  select(name, sleep_total:bodywt) %>%  # Select variables of interest
  filter_all(any_vars(.< 0.1))          # Filter all rows in selected variables with values less than 0.1

#Note that that any_vars statement is equivalent to OR. Correspondingly, all_vars statements is
# equivalent to AND, as shown in the code below.

msleep %>%                                    #Take msleep dataset, and then
  select(name, sleep_total:bodywt, -awake) %>% # Select variables of interest; deselect awake column
  filter_all(all_vars(. > 1))                  # Filter rows with all values greater than 1

#2. filter_if

msleep %>% 
  select(name:order, sleep_total:sleep_rem) %>% 
  filter_if(is.character, any_vars(is.na(.)))

#3. filter_at
# Select option1:
msleep %>% 
  select(name, sleep_total:sleep_rem, brainwt:bodywt) %>% 
  filter_at(vars(sleep_total, sleep_rem), all_vars(.>5))

# Select option2:
msleep %>% 
  select(name, sleep_total:sleep_rem, brainwt:bodywt) %>% 
  filter_at(vars(contains("sleep")), all_vars(.>5))
