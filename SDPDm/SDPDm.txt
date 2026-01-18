# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Spatial dynamic panel data lag model with fixed effects maximum likelihood estimation Use SDPDm (SDPDmod) With (In) R Software
install.packages("SDPDmod")
library("SDPDmod")
# Estimates Spatial dynamic panel data lag model with fixed effects maximum likelihood estimation Use SDPDm (SDPDmod) With (In) R Software
SDPDm = read.csv("https://raw.githubusercontent.com/timbulwidodostp/SDPDm/main/SDPDm/SDPDm.csv", sep = ";")
SDPDm <- SDPDm
SDPDm$logc <- log(SDPDm$sales)
SDPDm$logp <- log(SDPDm$price/SDPDm$cpi)
SDPDm$logy <- log(SDPDm$ndi/SDPDm$cpi)
SDPDm$lpm <- log(SDPDm$pimin/SDPDm$cpi)
SDPDm_ = read.csv("https://raw.githubusercontent.com/timbulwidodostp/SDPDm_/main/SDPDm_/SDPDm_.csv", sep = ";")
SDPDm_ <- as.matrix(SDPDm_)
str(SDPDm_)
SDPDm_ <- rownor(SDPDm_)
isrownor(SDPDm_)
SDPDm_1 <- SDPDm(formula = logc ~ logp+logy, data = SDPDm, W = SDPDm_, index = c("state","year"), model = "sar", effect = "individual", LYtrans = TRUE)
summary(SDPDm_1)
SDPDm_2 <- SDPDm(formula = logc ~ logp+logy, data = SDPDm, W = SDPDm_, index = c("state","year"), model = "sdm", 
effect = "twoways", LYtrans = TRUE, dynamic = TRUE, tlaginfo=list(ind = NULL, tl = TRUE, stl = TRUE))
summary(SDPDm_2)
# Spatial dynamic panel data lag model with fixed effects maximum likelihood estimation Use SDPDm (SDPDmod) With (In) R Software
# Olah Data Semarang
# WhatsApp : +6285227746673
# IG : @olahdatasemarang_
# Finished