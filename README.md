# Before the Aid: Federal Disaster Declarations, State Policy, and Governance Failures
[![DOI](https://zenodo.org/badge/1248393113.svg)](https://doi.org/10.5281/zenodo.20530640)

Nadia B. Ahmad | Yale School of the Environment | 2026

## Overview
Replication code and data documentation for a three-chapter empirical 
dissertation examining recognition inequity in federal disaster 
declarations under the Robert T. Stafford Disaster Relief and 
Emergency Assistance Act.

## Chapters

**Chapter 1: Social Vulnerability and Federal Disaster Declarations, 2000–2024**  
SVI theme decomposition and Random Forest analysis of declaration equity across U.S. counties.  
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nadiabahmad/disaster-declarations/blob/main/chapter_1/Chapter_1.ipynb)

**Chapter 2: Bounded Reform: State Environmental Justice Frameworks and the Federal Disaster Recognition Gap**  
Callaway-Sant'Anna staggered difference-in-differences analysis of state EJ frameworks and the federal declaration gap.  
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nadiabahmad/disaster-declarations/blob/main/chapter_2/Chapter_2.ipynb)

**Chapter 3: A Taxonomy of Governance Failures in Federal Disaster Mitigation**  
Six-type governance failure taxonomy benchmarked against the Sendai Framework for Disaster Risk Reduction.  
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/nadiabahmad/disaster-declarations/blob/main/chapter_3/Chapter_3.ipynb)


## Data Access & Sources

The datasets used in this dissertation are categorized into public and licensed datasets:

### Public Datasets (Included in Repository)
The following public datasets are tracked in this repository under the `data/` directory:
- **FEMA OpenFEMA Disaster Declarations (2000–2024)**
  - `DisasterDeclarationsSummaries.csv`
- **FEMA Hazard Mitigation Assistance**
  - `HazardMitigationAssistanceProjects.csv`
  - `HazardMitigationPlanStatuses.csv`
- **CDC/ATSDR Social Vulnerability Index (2010–2022)**
  - `SVI_2000_US_county.csv`
  - `SVI_2010_US_county.csv`
  - `SVI_2014_US_county.csv`
  - `SVI_2016_US_county.csv`
  - `SVI_2018_US_county.csv`
  - `SVI_2020_US_county.csv`
  - `SVI_2022_US_county.csv`
- **FEMA National Risk Index**
  - `National_Risk_Index_Counties.csv`
  - `NRI_metadata_December2025.pdf`
  - `fema_national-risk-index_technical-documentation.pdf`
- **USDA Rural-Urban Continuum Codes (2023)**
  - `Ruralurbancontinuumcodes2023.csv`
- **NOAA Coastal Counties**
  - `Coastal Counties.xlsx`
- **State EJ Frameworks Inventory**
  - `Article_2_-_State_EJ_Framework_Inventory_v4.xlsx`
- **US Census Bureau TIGER/Line Shapefiles (2022)**
  - `cb_2022_us_county_500k.zip` (Source: [census.gov](https://www2.census.gov/geo/tiger/GENZ2022/shp/cb_2022_us_county_500k.zip))
  - `cb_2022_us_state_500k.zip` (Source: [census.gov](https://www2.census.gov/geo/tiger/GENZ2022/shp/cb_2022_us_state_500k.zip))

### Licensed Datasets (Excluded)
The following datasets are used in the analysis but require an active license to access. They are **not** included in this repository:
- **SHELDUS v24.0 (ASU)**: Requires an active subscription from [SHELDUS](https://cemhs.asu.edu/sheldus/). 
  - Excluded files:
    - `direct_loss_aggregated_output_28320.csv`
    - `SHELDUS_Data_Documentation.pdf`

#### SHELDUS Data Structure & Mock Data
For users attempting to reproduce the analysis with their own SHELDUS export, the expected format of `direct_loss_aggregated_output_28320.csv` is as follows:

**Columns:**
`StateName`, `CountyName`, `County_FIPS`, `Year`, `Hazard`, `Fatalities`, `FatalitiesPerCapita`, `Fatalities_Duration`, `Injuries`, `InjuriesPerCapita`, `Injuries_Duration`, `CropDmg`, `CropDmg(ADJ 2024)`, `CropDmgPerCapita`, `Crop_Damage_Duration`, `PropertyDmg`, `PropertyDmg(ADJ 2024)`, `PropertyDmgPerCapita`, `Property_Damage_Duration`, `Duration_Days`, `Records`

**Mock Data Example:**
| StateName      | CountyName | County_FIPS | Year | Hazard         | Fatalities | PropertyDmg  | PropertyDmg(ADJ 2024) |
|----------------|------------|-------------|------|----------------|------------|--------------|-----------------------|
| SOUTH CAROLINA | Abbeville  | 45001       | 2000 | Winter Weather | 0.50000    | 0.00000      | 0.00000               |
| SOUTH CAROLINA | Abbeville  | 45001       | 2002 | Winter Weather | 0.00000    | 5000000.00000| 8884880.58568         |
| SOUTH CAROLINA | Abbeville  | 45001       | 2003 | Tornado        | 0.00000    | 21000.00000  | 36484.98955           |
| SOUTH CAROLINA | Abbeville  | 45001       | 2004 | Flooding       | 0.00000    | 82000.00000  | 138769.69980          |

## Reproduction Instructions

### Run Order
The Jupyter notebooks for each chapter are independent and belong to the same paper. They can be run in any order. Each notebook is contained within its own respective `chapter_X/` folder.

### Running Locally with `uv` (Recommended)
We recommend using [uv](https://github.com/astral-sh/uv), a fast Python package installer and resolver, to run the notebooks locally.

1. **Install `uv`** (if not already installed):
   You can install `uv` by running the command below for your operating system, or refer to the [uv installation guide](https://docs.astral.sh/uv/getting-started/installation/) for other installation options.
   - **macOS & Linux**:
     ```bash
     curl -LsSf https://astral-sh.uv/install.sh | sh
     ```
   - **Windows (PowerShell)**:
     ```powershell
     powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
     ```
2. **Clone the repository**:
   ```bash
   git clone https://github.com/nadiabahmad/disaster-declarations.git
   cd disaster-declarations
   ```
3. **Launch Jupyter Lab**:
   Running this command will automatically sync all the dependencies defined in `pyproject.toml` and `uv.lock` and start the Jupyter Lab server:
   ```bash
   uv run jupyter lab
   ```
   *(Alternatively, if you prefer traditional Jupyter Notebooks, run `uv run jupyter notebook`)*

### Running in Google Colab
You can run any of the notebooks directly in Google Colab without setting up a local environment.

1. **Open in Colab**: Click the "Open In Colab" button next to any chapter under the [Chapters](#chapters) section, or use these direct links:
   - [Run Chapter 1 in Colab](https://colab.research.google.com/github/nadiabahmad/disaster-declarations/blob/main/chapter_1/Chapter_1.ipynb)
   - [Run Chapter 2 in Colab](https://colab.research.google.com/github/nadiabahmad/disaster-declarations/blob/main/chapter_2/Chapter_2.ipynb)
   - [Run Chapter 3 in Colab](https://colab.research.google.com/github/nadiabahmad/disaster-declarations/blob/main/chapter_3/Chapter_3.ipynb)

2. **Repository Access (GitHub Token)**:
   Since the project needs to load datasets from the `data/` directory, the notebooks contain a cell that prompts you for a GitHub Personal Access Token (`gh_token`) to clone the repository's files into the Colab environment.
   - **For public repositories**: If the repository is public, you can leave the token field blank or click enter to proceed.
   - **For private repositories**: Generate a GitHub Personal Access Token (Classic with `repo` scope) from [GitHub Token Settings](https://github.com/settings/tokens) and paste it into the prompt.

3. **Uploading the Licensed SHELDUS Dataset**:
   The SHELDUS dataset is restricted/licensed and is not checked into this repository. When you execute the data-loading cell in the notebooks, Google Colab will display an interactive upload widget:
   - Upload your licensed SHELDUS dataset (`direct_loss_aggregated_output_28320.csv` or similar) when prompted.

## Citation
Ahmad, Nadia B. (2026). Before the Aid: Federal Disaster Declarations,  State Policy, and Governance Failures. Doctoral Dissertation,  Yale School of the Environment.
