# TrainingAssessment

[![Stable](https://img.shields.io/badge/docs-stable-blue.svg)](https://fieldofnodes.github.io/TrainingAssessment.jl/stable/)
[![Dev](https://img.shields.io/badge/docs-dev-blue.svg)](https://fieldofnodes.github.io/TrainingAssessment.jl/dev/)
[![Build Status](https://github.com/fieldofnodes/TrainingAssessment.jl/actions/workflows/CI.yml/badge.svg?branch=main)](https://github.com/fieldofnodes/TrainingAssessment.jl/actions/workflows/CI.yml?query=branch%3Amain)

# TrainingAssessment

Welcome to the `TrainingAssessment` module! This Julia package is designed to assist in creating detailed assessments of training programs and individual skills. It provides tools for generating and exporting LaTeX-formatted documents that include skill assessments, training program analyses, and customizable training tables.

## Features

- **Skill Assessment Mapping**: Converts skill levels into color-coded LaTeX representations for easy visualization.
- **Comprehensive LaTeX Document Generation**: Generates LaTeX code for skill analysis documents, including headers, footers, and dynamic content.
- **Export to File**: Easily write the generated LaTeX assessment or training tables to files for integration into larger documents.

## Installation

To use `TrainingAssessment`, ensure that you have Julia installed on your system. You can add this module to your Julia environment by including it in your project or environment:

```julia
] add https://github.com/your-repo/TrainingAssessment
```

## Usage

Begin by importing the module into your Julia environment:

```julia
using TrainingAssessment
```

### Generating a Skill Assessment Document

To generate a LaTeX-formatted skill assessment from a training assessment file, use the `write_training_assessment_to_file` function:

```julia
write_training_assessment_to_file("assessment.tex", "input_assessment.csv")
```

This function reads a CSV file containing the training assessment data, processes the skills and their corresponding levels, and writes the LaTeX code for the assessment document to a specified file.

### Mapping Skills to LaTeX Colors

The `map_to_latex_color` function maps a numeric skill level (0-5) to a corresponding LaTeX color representation:

```julia
color_code = map_to_latex_color(3)  # Returns "\\cyellow" for skill level 3
```

This can be used to visually represent skill levels in LaTeX documents.

### Generating Training Tables

To create a table that allows for skill level input within a LaTeX document, use the `generate_table` function:

```julia
training_table = generate_table(ttd::TrainingTableData)
```

This function generates a LaTeX table that includes placeholders for current and desired skill levels, which can be filled out manually or programmatically.

### Writing the Table to a File

Once the table is generated, you can write it to a file using the `write_table_to_file` function:

```julia
write_table_to_file("training_table.tex", ttd::TrainingTableData)
```

This will create a `.tex` file with the generated table content, ready to be included in a LaTeX document.

### Example Usage

```julia
# Assuming you have already generated `TrainingTableData` from the TrainingContent module
using TrainingContent

# Create some sample content titles
titles = ["Skill 1: Basics", "Skill 2: Intermediate", "Skill 3: Advanced"]

# Generate the training table data
training_data = generate_TrainingTableData(titles; course_length=10)

# Generate the LaTeX training log table as a string
latex_training_log = generate_table(training_data)

# Write the LaTeX training log table to a file
write_table_to_file("my_training_assessment.tex", training_data)
```

### Customizing the Document Layout

You can customize the appearance of the skill assessment document by modifying the `generate_document_header`, `generate_table_row`, and `generate_document_footer` functions. These functions control the structure and styling of the LaTeX document.

## Contributing

Contributions to `TrainingAssessment` are welcome! Please submit a pull request with your changes or open an issue if you encounter any problems.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## Contact

For questions, suggestions, or feedback, feel free to reach out via [GitHub Issues](https://github.com/your-repo/TrainingAssessment/issues).

---

This README provides an overview of the functionality within `TrainingAssessment`. For detailed examples and additional information, please refer to the module's source code and documentation.
