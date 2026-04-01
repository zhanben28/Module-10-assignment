# Module-10-assignment
library(ggplot2)
library(readr)
library(gridExtra)
hotdogs <- read_csv("http://datasets.flowingdata.com/hot-dog-contest-winners.csv")
head(hotdogs)
colnames(hotdogs) <- make.names(colnames(hotdogs))
colors <- ifelse(hotdogs$New.record == 1, "darkred", "grey")
barplot(hotdogs$Dogs.eaten, names.arg = hotdogs$Year, col=colors, border=NA, main = "Nathan's Hot Dog Eating Contest Results, 1980-2010", xlab="Year", ylab="Hot dogs and buns (HDBs) eaten")
ggplot(hotdogs) + geom_bar(aes(x=Year, y=Dogs.eaten, fill=factor(New.record)), stat="identity") + labs(title="Nathan's Hot Dog Eating Contest Results, 1980-2010", fill="New Record") + xlab("Year") + ylab("Hot dogs and buns (HDBs) eaten")
head(economics)
year <- function(x) as.POSIXlt(x)$year + 1900
economics$year <- year(economics$date)
head(economics)
plot1 <- qplot(date, unemploy / pop, data = economics, geom = "line")
plot1
plot2 <- qplot(date, uempmed, data = economics, geom = "line")
grid.arrange(plot1, plot2, ncol=2)
plot1 <- qplot(unemploy/pop, uempmed, data = economics, geom = c("point", "path"))
plot2 <- qplot(unemploy/pop, uempmed, data = economics, geom = c("point", "path"), color=year)
grid.arrange(plot1, plot2, ncol=2)
plot2
ggplot(economics, aes(x = date, y = psavert)) +
  geom_line(color = "steelblue") +
  labs(title = "US Personal Savings Rate Over Time", x = "Year", y = "Savings Rate (%)")
