# Multi-Scale Mobility Anomaly Detection

## Overview

This project analyzes human mobility patterns during normal and emergency periods using the YJMob100K dataset. We discovered something surprising: people actually become MORE predictable during emergencies, not more chaotic as commonly assumed.

## Key Findings

**Main Discovery**: During emergencies, daily behavior patterns become more structured while individual activities show only small increases in irregularity.

**Numbers That Matter**:
- Daily anomaly rates DECREASED from 8.2% to 7.4% during emergencies
- Individual trip anomalies increased slightly from 10.5% to 10.9%
- People delayed their daily start times by about 1 hour
- Spatial coverage reduced by 69% - people stuck to familiar places
- Social activities increased from 7.2% to 10.6%
- Dining and shopping activities decreased by 3-4%

## What We Studied

**Dataset**: 100 people tracked for 75 days (60 normal days + 15 emergency days)
**Records**: 136,175 mobility records across 10,495 locations
**Time**: 30-minute intervals throughout each day

## Primary Datasets
1. Human Mobility Dataset (YJMob100K)

Source: Zenodo - YJMob100K Dataset
Description: Large-scale GPS trajectory data covering normal and emergency periods
Files:

yjmob100k-dataset1.csv.gz - Business-as-usual mobility patterns (75 days)
yjmob100k-dataset2.csv.gz - Emergency behavior patterns (75 days)


Size: ~29M records across 25,000 users
Time Coverage: 150 days (Days 0-60: Normal, Days 61-75: Emergency)
Spatial Coverage: Metropolitan area with 500m × 500m grid cells

2. Point of Interest (POI) Dataset

Source: Zenodo - POI Categories
Description: Comprehensive POI data with functional categorization
Files:

cell_POIcat.csv.gz - POI locations and counts per grid cell
POI_datacategories.csv - POI category definitions and mappings


Coverage: 20,146 unique locations with 85 POI categories
Features: Spatial coordinates, POI counts, category classifications

Processed Scientific Datasets
3. Scientific Mobility Base Dataset

File: scientific_mobility_base_dataset.csv
Description: Core mobility data with integrated POI context and enhanced features
Features:

Temporal: Hour, time periods, day of week, weekend indicators
Spatial: Grid coordinates, distance from center, spatial zones
Contextual: Primary POI category, functional groups, density metrics
Behavioral: User ID, activity intensity, mobility patterns


Records: 2.5M+ mobility records
Users: 100 users (filtered for comprehensive analysis)

4. POI Presence Matrix Dataset

File: scientific_mobility_poi_matrix_dataset.csv
Description: Binary feature matrix for POI presence analysis
Features:

Binary indicators for top 20 POI categories
Binary indicators for all functional groups
Perfect for machine learning applications


Applications: Classification, clustering, anomaly detection

5. Functional Groups Dataset

File: scientific_mobility_functional_dataset.csv
Description: Mobility data with hierarchical functional categorization
Functional Categories:

Food Services, Retail Shopping, Transportation
Education, Healthcare, Entertainment
Services, Business, Religious, Other


Use Cases: Urban planning, service allocation, policy analysis

6. User Behavioral Profiles

File: scientific_user_profiles_dataset.csv
Description: Aggregated individual-level mobility characteristics
Metrics:

Activity: Total records, active days, intensity
Mobility: Radius, spatial coverage, distance preferences
Temporal: Weekend ratios, temporal diversity
Behavioral: Cluster assignments, change patterns


Applications: User segmentation, personalization, behavioral modeling

7. Location Characteristics Profiles

File: scientific_location_profiles_dataset.csv
Description: Place-based analysis of location attractiveness and usage
Metrics:

Popularity: Unique visitors, total visits, popularity scores
Temporal: Active hours, temporal span, weekend ratios
Spatial: Coordinates, distance from center
Context: Dominant POI categories, functional groups


Applications: Location recommendation, urban planning, service optimization

## Methods Used

**Two-Level Analysis**:
- Subset Level: Looking at individual trips and activities  
- Daily Level: Looking at complete daily behavior patterns

**Hidden Markov Models**: We identified 4 behavioral states:
- Routine: Regular daily activities
- Social: Meeting people and social activities  
- Crisis: Emergency-related behavior
- Exploration: Trying new places or activities

**Text Conversion**: We can convert movement data into readable sentences like:
"During Tuesday afternoon at 12:30, the user visited a Japanese restaurant in a high-density urban area and engaged in dining activities."

## How People Adapted During Emergency

**Where They Went**:
- 52% of usual locations were abandoned
- Only 7% new locations were explored
- People concentrated in central areas (40% to 60%)
- Avoided outer areas (dropped from 25% to 5%)

**When They Moved**:
- Started daily activities 1 hour later on average
- Peak activity time stayed the same (5:00 PM)
- Morning activities (6-9 AM) decreased significantly
- Late morning activities (11 AM-1 PM) increased

**What They Did**:
- Less dining out and shopping
- More social visits and essential services
- More focused on support and connectivity activities

## Individual Differences

**Most People (79%)**: Made moderate adjustments to their routines
**Some People (21%)**: Made extreme changes to their behavior

Example: One person's irregularity increased by 33%, completely changing from routine behavior to highly exploratory patterns.

## Why This Matters

**For Emergency Planning**:
- Resources should be concentrated in central, familiar areas
- Services can be scheduled around delayed start times  
- Plan for increased social support needs

**For Understanding Human Behavior**:
- Crises don't create chaos - they create structure
- People prioritize familiar places and essential connections
- Individual responses vary greatly even in the same emergency

## Technical Implementation

**Programming**: Python with standard data science libraries
**Models**: Hidden Markov Models for behavioral state detection
**Analysis**: Statistical testing to confirm behavioral changes
**Validation**: Compared multiple detection methods

**Performance**: 
- Processing time: 44 seconds per person
- Memory usage: 324 KB per person
- Detection accuracy: 75% of changes were statistically significant

## Files in This Repository

- Data loading and processing scripts
- Anomaly detection algorithms  
- Text-trajectory conversion tools
- Statistical analysis functions
- Visualization code for results
- Example notebooks showing how to use the tools

## Main Contributions

1. **New Framework**: First system to detect anomalies at multiple time scales simultaneously
2. **Surprising Finding**: Emergencies make people more predictable, not less
3. **Practical Tools**: Convert mobility data to readable explanations
4. **Real Applications**: Useful for emergency response and urban planning

## Getting Started

1. Download the YJMob100K dataset
2. Install Python with pandas, numpy, scikit-learn, and matplotlib
3. Run the main analysis script
4. Explore individual user patterns and emergency adaptations

## Results Summary

The research challenges the common assumption that emergencies create chaotic behavior. Instead, we found that people become more structured and predictable during crises, concentrating their activities in familiar areas and following more rigid daily routines. This has important implications for how we plan emergency responses and understand human behavior under stress.

## Future Work

- Apply to different types of emergencies and regions
- Develop real-time monitoring systems
- Integrate with other data sources like communications and economic indicators
- Create predictive models for emergency behavior

This work provides the first systematic evidence that emergency behavior is more structured than chaotic, offering new insights for researchers and practical tools for emergency managers and urban planners.
