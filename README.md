install_if_not_installed <- function(pkg, install_function = install.packages) {
  if (!requireNamespace(pkg, quietly = TRUE)) {
    if (identical(install_function, install.packages)) {
      install.packages(pkg)
    } else {
      install_function(pkg)
    }
  }
}

pkgs <- c("VariantAnnotation", "gwasglue", "dplyr", "tidyr", "CMplot")

install_if_not_installed("devtools")
install_if_not_installed("gwasglue", devtools::install_github("mrcieu/gwasglue", force = TRUE))
install_if_not_installed("BiocManager")
install_if_not_installed("VariantAnnotation", BiocManager::install)
install_if_not_installed("dplyr")
install_if_not_installed("tidyr")
install_if_not_installed("CMplot")

lapply(pkgs, function(pkg) { suppressMessages(library(pkg, character.only = TRUE, quietly = TRUE)) })
