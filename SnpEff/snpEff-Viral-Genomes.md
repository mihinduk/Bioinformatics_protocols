Creating a snpEff Database for Viral Genomes

  This guide provides step-by-step instructions for adding viral genomes to snpEff for variant annotation.

  Quick Reference Guide

  1. Download the GenBank file

  - Visit NCBI: https://www.ncbi.nlm.nih.gov/nuccore/[ACCESSION_NUMBER]
  - Click "Send to" > "File" > Format "GenBank" > Create File
  - Save as "genes.gbk"

  2. Create directory structure and copy files

  # Create directory
  mkdir -p /path/to/snpEff/data/[ACCESSION_NUMBER]

  # Move the GenBank file
  mv genes.gbk /path/to/snpEff/data/[ACCESSION_NUMBER]/

  3. Add genome to snpEff.config

  # [ACCESSION_NUMBER] (Virus Full Name strain STRAIN_NAME)
  [ACCESSION_NUMBER].genome: [VIRUS_ABBREVIATION]-[STRAIN]
  [ACCESSION_NUMBER].chromosomes: [ACCESSION_NUMBER]
  [ACCESSION_NUMBER].codonTable: Standard

  4. Build the database

  cd /path/to/snpEff
  java -jar snpEff.jar build -genbank -v -noCheckProtein [ACCESSION_NUMBER]

  5. Run annotation

  java -jar snpEff.jar [ACCESSION_NUMBER] input.vcf > output.ann.vcf

  Important Notes

  Common Errors

  - Protein verification failures: Nearly all viral genomes will have issues with protein verification
    - Solution: Always use -noCheckProtein flag during database build
    - Example error: Protein check: OK: 1 Not found: 9 Errors: 1 Error percentage: 50.0%
  - Missing protein.fa warning:
    - Message: WARNING_FILE_NOT_FOUND: Rare Amino Acid analysis: Cannot read protein sequence file
    - Solution: Safe to ignore; this is an optional analysis

  Naming Conventions

  - Genome name: Use standard virus abbreviation followed by strain
    - Examples: SINV-TR339, LGTV-TP21, HCoV-229E
  - Common virus abbreviations:
    - SINV: Sindbis virus
    - MAYV: Mayaro virus
    - LGTV: Langat virus
    - RRV: Ross River virus
    - HCoV: Human coronavirus

  Additional Build Options

  - -noCheckCds: Use if -noCheckProtein alone doesn't work
  - Complete command: java -jar snpEff.jar build -genbank -v -noCheckProtein -noCheckCds [ACCESSION_NUMBER]

  Example Database Builds

  Langat virus (AF253419.1)

  # AF253419.1 (Langat virus strain TP21)
  AF253419.1.genome: LGTV-TP21
  AF253419.1.chromosomes: AF253419.1
  AF253419.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein AF253419.1

  Mayaro virus (MK573243.1)

  # MK573243.1 (Mayaro virus strain IQU2950)
  MK573243.1.genome: MAYV-IQU2950
  MK573243.1.chromosomes: MK573243.1
  MK573243.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein MK573243.1

  Sindbis virus (OR882082.1)

  # OR882082.1 (Sindbis virus strain TR339)
  OR882082.1.genome: SINV-TR339
  OR882082.1.chromosomes: OR882082.1
  OR882082.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein OR882082.1

  Ross River virus (GQ433359.1)

  # GQ433359.1 (Ross River virus strain T48)
  GQ433359.1.genome: RRV-T48
  GQ433359.1.chromosomes: GQ433359.1
  GQ433359.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein GQ433359.1

  Human coronavirus (AF304460.1)

  # AF304460.1 (Human coronavirus 229E)
  AF304460.1.genome: HCoV-229E
  AF304460.1.chromosomes: AF304460.1
  AF304460.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein AF304460.1

> Could you please save this in a format that I can upload to github with the appropriate markup to make it clear?
  Please change Creating a snpEff Database for Viral Genomes to "Creating a snpEff Database Entry for Viral Genomes"

⏺ # Creating a snpEff Database Entry for Viral Genomes

  This guide provides step-by-step instructions for adding viral genomes to snpEff for variant annotation.

  ## Quick Reference Guide

  ### 1. Download the GenBank file
  - Visit NCBI: `https://www.ncbi.nlm.nih.gov/nuccore/[ACCESSION_NUMBER]`
  - Click "Send to" > "File" > Format "GenBank" > Create File
  - Save as "genes.gbk"

  ### 2. Create directory structure and copy files
  ```bash
  # Create directory
  mkdir -p /path/to/snpEff/data/[ACCESSION_NUMBER]

  # Move the GenBank file
  mv genes.gbk /path/to/snpEff/data/[ACCESSION_NUMBER]/

  3. Add genome to snpEff.config

  # [ACCESSION_NUMBER] (Virus Full Name strain STRAIN_NAME)
  [ACCESSION_NUMBER].genome: [VIRUS_ABBREVIATION]-[STRAIN]
  [ACCESSION_NUMBER].chromosomes: [ACCESSION_NUMBER]
  [ACCESSION_NUMBER].codonTable: Standard

  4. Build the database

  cd /path/to/snpEff
  java -jar snpEff.jar build -genbank -v -noCheckProtein [ACCESSION_NUMBER]

  5. Run annotation

  java -jar snpEff.jar [ACCESSION_NUMBER] input.vcf > output.ann.vcf

  Important Notes

  Common Errors

  - Protein verification failures: Nearly all viral genomes will have issues with protein verification
    - Solution: Always use -noCheckProtein flag during database build
    - Example error: Protein check: OK: 1 Not found: 9 Errors: 1 Error percentage: 50.0%
  - Missing protein.fa warning:
    - Message: WARNING_FILE_NOT_FOUND: Rare Amino Acid analysis: Cannot read protein sequence file
    - Solution: Safe to ignore; this is an optional analysis

  Naming Conventions

  - Genome name: Use standard virus abbreviation followed by strain
    - Examples: SINV-TR339, LGTV-TP21, HCoV-229E
  - Common virus abbreviations:
    - SINV: Sindbis virus
    - MAYV: Mayaro virus
    - LGTV: Langat virus
    - RRV: Ross River virus
    - HCoV: Human coronavirus

  Additional Build Options

  - -noCheckCds: Use if -noCheckProtein alone doesn't work
  - Complete command: java -jar snpEff.jar build -genbank -v -noCheckProtein -noCheckCds [ACCESSION_NUMBER]

  Example Database Builds

  Langat virus (AF253419.1)

  # AF253419.1 (Langat virus strain TP21)
  AF253419.1.genome: LGTV-TP21
  AF253419.1.chromosomes: AF253419.1
  AF253419.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein AF253419.1

  Mayaro virus (MK573243.1)

  # MK573243.1 (Mayaro virus strain IQU2950)
  MK573243.1.genome: MAYV-IQU2950
  MK573243.1.chromosomes: MK573243.1
  MK573243.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein MK573243.1

  Sindbis virus (OR882082.1)

  # OR882082.1 (Sindbis virus strain TR339)
  OR882082.1.genome: SINV-TR339
  OR882082.1.chromosomes: OR882082.1
  OR882082.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein OR882082.1

  Ross River virus (GQ433359.1)

  # GQ433359.1 (Ross River virus strain T48)
  GQ433359.1.genome: RRV-T48
  GQ433359.1.chromosomes: GQ433359.1
  GQ433359.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein GQ433359.1

  Human coronavirus (AF304460.1)

  # AF304460.1 (Human coronavirus 229E)
  AF304460.1.genome: HCoV-229E
  AF304460.1.chromosomes: AF304460.1
  AF304460.1.codonTable: Standard

  # Build command:
  java -jar snpEff.jar build -genbank -v -noCheckProtein AF304460.1
