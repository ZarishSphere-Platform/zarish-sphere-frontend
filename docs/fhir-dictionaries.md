# FHIR Dictionaries & Metadata

Complete FHIR R4 value sets, code systems, and metadata for form building.

## Table of Contents

- [Administrative Value Sets](#administrative-value-sets)
- [Clinical Value Sets](#clinical-value-sets)
- [Observation Concepts](#observation-concepts)
- [Condition Codes](#condition-codes)
- [Procedure Codes](#procedure-codes)
- [Medication Codes](#medication-codes)

## Administrative Value Sets

### Administrative Gender

**ValueSet URL:** `http://hl7.org/fhir/ValueSet/administrative-gender`

| Code | Display | Definition |
|------|---------|------------|
| male | Male | Male gender |
| female | Female | Female gender |
| other | Other | Other gender |
| unknown | Unknown | Unknown gender |

### Marital Status

**ValueSet URL:** `http://hl7.org/fhir/ValueSet/marital-status`

| Code | Display |
|------|---------|
| A | Annulled |
| D | Divorced |
| I | Interlocutory |
| L | Legally Separated |
| M | Married |
| P | Polygamous |
| S | Never Married |
| T | Domestic partner |
| U | unmarried |
| W | Widowed |

### Contact Relationship

**ValueSet URL:** `http://hl7.org/fhir/ValueSet/patient-contactrelationship`

| Code | Display |
|------|---------|
| C | Emergency Contact |
| E | Employer |
| F | Federal Agency |
| I | Insurance Company |
| N | Next-of-Kin |
| S | State Agency |
| U | Unknown |

## Clinical Value Sets

### Blood Type (SNOMED CT)

**System:** `http://snomed.info/sct`

| SNOMED Code | Display | Common Name |
|-------------|---------|-------------|
| 112144000 | Blood group A Rh(D) positive | A+ |
| 165743006 | Blood group A Rh(D) negative | A- |
| 112149005 | Blood group B Rh(D) positive | B+ |
| 165747007 | Blood group B Rh(D) negative | B- |
| 112152002 | Blood group AB Rh(D) positive | AB+ |
| 165750005 | Blood group AB Rh(D) negative | AB- |
| 58460004 | Blood group O Rh(D) positive | O+ |
| 165746003 | Blood group O Rh(D) negative | O- |

### Encounter Status

**System:** `http://hl7.org/fhir/encounter-status`

| Code | Display | Definition |
|------|---------|------------|
| planned | Planned | The Encounter has not yet started |
| arrived | Arrived | The Patient is present for the encounter |
| triaged | Triaged | The patient has been assessed |
| in-progress | In Progress | The Encounter has begun |
| onleave | On Leave | The Encounter has been suspended |
| finished | Finished | The Encounter has ended |
| cancelled | Cancelled | The Encounter was cancelled |
| entered-in-error | Entered in Error | This instance should not have been part of this patient's medical record |
| unknown | Unknown | The encounter status is unknown |

### Encounter Class

**System:** `http://terminology.hl7.org/CodeSystem/v3-ActCode`

| Code | Display | Definition |
|------|---------|------------|
| AMB | Ambulatory | A comprehensive term for health care provided in a healthcare facility (e.g. a practitioneraTMs office, clinic setting, or hospital) on a nonresident basis |
| EMER | Emergency | A patient encounter that takes place at a dedicated healthcare service delivery location where the patient receives immediate evaluation and treatment |
| FLD | Field | A patient encounter that takes place both outside a dedicated service delivery location and outside a patient's residence |
| HH | Home health | Healthcare encounter that takes place in the residence of the patient or a designee |
| IMP | Inpatient encounter | A patient encounter where a patient is admitted by a hospital or equivalent facility |
| ACUTE | Inpatient acute | An acute inpatient encounter |
| NONAC | Inpatient non-acute | Any category of inpatient encounter except 'acute' |
| OBSENC | Observation encounter | An encounter where the patient usually will start in different encounter, such as one in the emergency department but then transition to this type of encounter because they require a significant period of treatment and monitoring |
| PRENC | Pre-admission | A patient encounter where patient is scheduled or planned to receive service delivery in the future |
| SS | Short stay | An encounter where the patient is admitted to a health care facility for a predetermined length of time, usually less than 24 hours |
| VR | Virtual | A patient encounter where the patient and the practitioner(s) are not in the same physical location |

## Observation Concepts

### Vital Signs (LOINC)

**System:** `http://loinc.org`

| LOINC Code | Display | Unit | Normal Range |
|------------|---------|------|--------------|
| 8310-5 | Body temperature | °C | 36.5-37.5 |
| 8867-4 | Heart rate | beats/min | 60-100 |
| 9279-1 | Respiratory rate | breaths/min | 12-20 |
| 8480-6 | Systolic blood pressure | mmHg | 90-120 |
| 8462-4 | Diastolic blood pressure | mmHg | 60-80 |
| 2708-6 | Oxygen saturation | % | 95-100 |
| 29463-7 | Body weight | kg | - |
| 8302-2 | Body height | cm | - |
| 39156-5 | Body mass index | kg/m² | 18.5-24.9 |
| 8478-0 | Mean blood pressure | mmHg | 70-100 |

### Laboratory Results (LOINC)

| LOINC Code | Display | Unit | Reference Range |
|------------|---------|------|-----------------|
| 718-7 | Hemoglobin | g/dL | M: 13.5-17.5, F: 12-15.5 |
| 789-8 | Erythrocytes | 10*6/µL | M: 4.5-5.9, F: 4.1-5.1 |
| 6690-2 | Leukocytes | 10*3/µL | 4.5-11 |
| 777-3 | Platelets | 10*3/µL | 150-400 |
| 2345-7 | Glucose | mg/dL | 70-100 (fasting) |
| 2160-0 | Creatinine | mg/dL | M: 0.7-1.3, F: 0.6-1.1 |
| 3094-0 | Urea nitrogen | mg/dL | 7-20 |
| 2951-2 | Sodium | mmol/L | 136-145 |
| 2823-3 | Potassium | mmol/L | 3.5-5.0 |
| 2075-0 | Chloride | mmol/L | 98-107 |

## Condition Codes

### ICD-10 Common Conditions

**System:** `http://hl7.org/fhir/sid/icd-10`

| ICD-10 Code | Display |
|-------------|---------|
| E11.9 | Type 2 diabetes mellitus without complications |
| I10 | Essential (primary) hypertension |
| J45.909 | Unspecified asthma, uncomplicated |
| M79.3 | Panniculitis, unspecified |
| R50.9 | Fever, unspecified |
| J06.9 | Acute upper respiratory infection, unspecified |
| K21.9 | Gastro-esophageal reflux disease without esophagitis |
| M25.50 | Pain in unspecified joint |
| R51 | Headache |
| R10.9 | Unspecified abdominal pain |

### SNOMED CT Clinical Findings

**System:** `http://snomed.info/sct`

| SNOMED Code | Display |
|-------------|---------|
| 38341003 | Hypertensive disorder |
| 73211009 | Diabetes mellitus |
| 195967001 | Asthma |
| 386661006 | Fever |
| 49727002 | Cough |
| 25064002 | Headache |
| 21522001 | Abdominal pain |
| 267036007 | Dyspnea |
| 422587007 | Nausea |
| 422400008 | Vomiting |

## Procedure Codes

### CPT Codes (Common Procedures)

**System:** `http://www.ama-assn.org/go/cpt`

| CPT Code | Display |
|----------|---------|
| 99213 | Office visit, established patient, 20-29 minutes |
| 99214 | Office visit, established patient, 30-39 minutes |
| 99215 | Office visit, established patient, 40-54 minutes |
| 99203 | Office visit, new patient, 30-44 minutes |
| 99204 | Office visit, new patient, 45-59 minutes |
| 99205 | Office visit, new patient, 60-74 minutes |
| 99281 | Emergency department visit, self limited |
| 99282 | Emergency department visit, low to moderately severe |
| 99283 | Emergency department visit, moderately severe |
| 99284 | Emergency department visit, high severity |
| 99285 | Emergency department visit, high severity with significant threat |

### SNOMED CT Procedures

**System:** `http://snomed.info/sct`

| SNOMED Code | Display |
|-------------|---------|
| 5880005 | Physical examination |
| 171207006 | Depression screening |
| 171222001 | Hypertension screening |
| 171241003 | Diabetes screening |
| 410620009 | Well child visit |
| 439708006 | Home visit |
| 185349003 | Encounter for check up |
| 185345009 | Encounter for symptom |

## Medication Codes

### RxNorm Common Medications

**System:** `http://www.nlm.nih.gov/research/umls/rxnorm`

| RxNorm Code | Display | Generic Name |
|-------------|---------|--------------|
| 197361 | Metformin 500 MG Oral Tablet | Metformin |
| 314076 | Lisinopril 10 MG Oral Tablet | Lisinopril |
| 197805 | Amlodipine 5 MG Oral Tablet | Amlodipine |
| 197884 | Atorvastatin 20 MG Oral Tablet | Atorvastatin |
| 198033 | Omeprazole 20 MG Delayed Release Oral Capsule | Omeprazole |
| 197511 | Levothyroxine 50 MCG Oral Tablet | Levothyroxine |
| 198033 | Omeprazole 20 MG Delayed Release Oral Capsule | Omeprazole |

## Form Building Metadata

### Complete Patient Form Definition

```json
{
  "resourceType": "Questionnaire",
  "id": "patient-registration-complete",
  "title": "Complete Patient Registration",
  "status": "active",
  "item": [
    {
      "linkId": "demographics",
      "text": "Demographics",
      "type": "group",
      "item": [
        {
          "linkId": "mrn",
          "text": "Medical Record Number",
          "type": "string",
          "required": true
        },
        {
          "linkId": "name",
          "text": "Name",
          "type": "group",
          "item": [
            {
              "linkId": "firstName",
              "text": "First Name",
              "type": "string",
              "required": true
            },
            {
              "linkId": "middleName",
              "text": "Middle Name",
              "type": "string"
            },
            {
              "linkId": "lastName",
              "text": "Last Name",
              "type": "string",
              "required": true
            }
          ]
        },
        {
          "linkId": "gender",
          "text": "Gender",
          "type": "choice",
          "required": true,
          "answerValueSet": "http://hl7.org/fhir/ValueSet/administrative-gender"
        },
        {
          "linkId": "birthDate",
          "text": "Date of Birth",
          "type": "date",
          "required": true
        },
        {
          "linkId": "maritalStatus",
          "text": "Marital Status",
          "type": "choice",
          "answerValueSet": "http://hl7.org/fhir/ValueSet/marital-status"
        }
      ]
    },
    {
      "linkId": "contact",
      "text": "Contact Information",
      "type": "group",
      "item": [
        {
          "linkId": "phone",
          "text": "Phone Number",
          "type": "string"
        },
        {
          "linkId": "email",
          "text": "Email",
          "type": "string"
        },
        {
          "linkId": "address",
          "text": "Address",
          "type": "group",
          "item": [
            {
              "linkId": "line",
              "text": "Street Address",
              "type": "string"
            },
            {
              "linkId": "city",
              "text": "City",
              "type": "string"
            },
            {
              "linkId": "state",
              "text": "State/Province",
              "type": "string"
            },
            {
              "linkId": "postalCode",
              "text": "Postal Code",
              "type": "string"
            },
            {
              "linkId": "country",
              "text": "Country",
              "type": "string"
            }
          ]
        }
      ]
    },
    {
      "linkId": "clinical",
      "text": "Clinical Information",
      "type": "group",
      "item": [
        {
          "linkId": "bloodType",
          "text": "Blood Type",
          "type": "choice",
          "answerOption": [
            {"valueCoding": {"code": "A+", "display": "A Positive"}},
            {"valueCoding": {"code": "A-", "display": "A Negative"}},
            {"valueCoding": {"code": "B+", "display": "B Positive"}},
            {"valueCoding": {"code": "B-", "display": "B Negative"}},
            {"valueCoding": {"code": "AB+", "display": "AB Positive"}},
            {"valueCoding": {"code": "AB-", "display": "AB Negative"}},
            {"valueCoding": {"code": "O+", "display": "O Positive"}},
            {"valueCoding": {"code": "O-", "display": "O Negative"}}
          ]
        }
      ]
    }
  ]
}
```

## Download Complete Dictionaries

- [FHIR Value Sets (JSON)](fhir-valuesets.json)
- [LOINC Observations (CSV)](loinc-observations.csv)
- [ICD-10 Codes (CSV)](icd10-codes.csv)
- [SNOMED CT Concepts (CSV)](snomed-concepts.csv)
- [RxNorm Medications (CSV)](rxnorm-medications.csv)

## Usage in Form Builders

### React Hook Form Example

```typescript
import { useForm } from 'react-hook-form';

const PatientForm = () => {
  const { register, handleSubmit } = useForm();
  
  const onSubmit = (data) => {
    // Submit to API
    fetch('/api/v1/patients', {
      method: 'POST',
      body: JSON.stringify(data)
    });
  };
  
  return (
    <form onSubmit={handleSubmit(onSubmit)}>
      <select {...register('gender')}>
        <option value="male">Male</option>
        <option value="female">Female</option>
        <option value="other">Other</option>
        <option value="unknown">Unknown</option>
      </select>
      
      <select {...register('bloodType')}>
        <option value="A+">A Positive</option>
        <option value="A-">A Negative</option>
        <option value="B+">B Positive</option>
        <option value="B-">B Negative</option>
        <option value="AB+">AB Positive</option>
        <option value="AB-">AB Negative</option>
        <option value="O+">O Positive</option>
        <option value="O-">O Negative</option>
      </select>
      
      <button type="submit">Register Patient</button>
    </form>
  );
};
```

---

**Last Updated:** 2025-11-25  
**FHIR Version:** R4  
**Standards:** HL7 FHIR, LOINC, SNOMED CT, ICD-10, RxNorm
