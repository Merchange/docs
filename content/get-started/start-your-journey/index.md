rm(list = ls())
setwd("file location")
data <- read.csv("file.csv",sep=",",header=TRUE,row.names=1)
data <- as.matrix(data)
Sum <- apply(data,2,sum)
new_data<-as.data.frame(matrix(NA,ncol = ncol(data),nrow = nrow(data)))
rownames(new_data)=rownames(data)
colnames(new_data)=colnames(data)
for(i in 1:nrow(data)){
  for(j in 1:ncol(data)){
    new_data[i,j]=data[i,j]*1000/Sum[j]
  }
}
write.table(new_data,file="Sumnor_hip.csv",sep=",",na=" ",row.names = TRUE, col.names = TRUE)

