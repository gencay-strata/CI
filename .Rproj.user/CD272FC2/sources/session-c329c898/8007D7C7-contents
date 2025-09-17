# R/train_model.R

# Create dummy student data
student_data <- data.frame(
  age = c(21, 22, 23, 24, 25),
  gender = c("M", "F", "F", "M", "F"),   # kept, but not used in the model
  score = c(85, 90, 78, 88, 92),
  passed = c(1, 1, 0, 1, 1)
)

# Keep only complete rows
student_data <- na.omit(student_data)

# Define predictor variables actually used in the model
predictor_vars <- c("age", "score")

# Sanity check: all predictors should be numeric
if (!all(sapply(student_data[, predictor_vars], is.numeric))) {
  stop("All predictor variables must be numeric.")
}

# Fit logistic regression
model <- glm(passed ~ age + score, data = student_data, family = binomial)

# Predict
predictions <- predict(model, type = "response")
predicted_class <- ifelse(predictions > 0.5, 1, 0)

# Return output as list
output <- list(
  model = model,
  predictions = predictions,
  predicted_class = predicted_class,
  student_data = student_data
)

# Save output as .rds file (optional)
saveRDS(output, file = "model_output.rds")
