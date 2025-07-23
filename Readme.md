Java FHIR Validator: Null Message ID Bug

This repository demonstrates a bug in the Java FHIR Validator where the messageId field is unexpectedly null. The validator should always produce a non-null identifier for each validation message.

* Run the validator with -show-message-ids

`java -jar validator_cli.jar . -show-message-ids -advisor-file advisor.json`

🔍 Observed Behavior

Validator output includes entries like this:

```
-- ./StructureDefinition-TestEncounterProfile.json -------------------------------------------------------
*FAILURE*: 1 errors, 0 warnings, 0 notes
  Error @ StructureDefinition.differential.element[0].pattern.ofType(Coding).code (line 18, col10): Unknown code '3' in the CodeSystem 'http://example.org/CodeSystem/TestCodeSystem' version 'null' {null}
----------------------------------------------------------------------------------------------------------
```

Notice that "messageId" is {null}.

⸻

✅ Expected Behavior

Each validation message should include a unique, non-null messageId property.