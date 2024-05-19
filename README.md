# lab-mandaroty03

## Scenario 1: User Authentication Tests

Original Test Case (Pseudocode):

```
TEST UserAuthentication
  ASSERT_TRUE(authenticate("validUser", "validPass"), "Should succeed with correct credentials")
  ASSERT_FALSE(authenticate("validUser", "wrongPass"), "Should fail with wrong credentials")
END TEST
```
* Analysis Report: En este caso, se puede separar la logíca del test en dos test (success and failed)

```
TEST UserAuthenticationSuccess
  ASSERT_TRUE(authenticate("validUser", "validPass"), "Should succeed with correct credentials")
END TEST


TEST UserAuthenticationFailed
    ASSERT_FALSE(authenticate("validUser", "wrongPass"), "Should fail with wrong credentials")
END TEST
```

## Scenario 2: Data Processing Functions

Original Test Case (Pseudocode):

```
TEST DataProcessing
  DATA data = fetchData()
  TRY
    processData(data)
    ASSERT_TRUE(data.processedSuccessfully, "Data should be processed successfully")
  CATCH error
    ASSERT_EQUALS("Data processing error", error.message, "Should handle processing errors")
  END TRY
END TEST
```
* Analysis Report: Podemos generar un test para probar el happy path, otro test para comprobar cuando se lanza una exception
```
TEST DataProcessingHappyPath
  DATA data = fetchData()
  processData(data)
  ASSERT_TRUE(data.processedSuccessfully, "Data should be processed successfully")
END TEST

TEST DataProcessing
  DATA data = fetchData()
  TRY
    processData(data) //throws an exception
    ASSERT_THROWS(Exception, processData(data))
  CATCH error
    ASSERT_EQUALS("Data processing error", error.message, "Should handle processing errors")
  END TRY
END TEST
```


## Scenario 3: UI Responsiveness

Original Test Case (Pseudocode):

```
TEST UIResponsiveness
  UI_COMPONENT uiComponent = setupUIComponent(1024)
  ASSERT_TRUE(uiComponent.adjustsToScreenSize(1024), "UI should adjust to width of 1024 pixels")
END TEST
```
* Analysis Report: Podemos agregar otros caso o table donde se varie el valor de pixels para comprobar que la interfaz se comporta responsive


```
TEST UIResponsiveness
  UI_COMPONENT uiComponent = setupUIComponent(pixel)
  ASSERT_TRUE(uiComponent.adjustsToScreenSize(pixel), "UI should adjust to width of" + pixel + "pixels")

  WHERE
  pixel
  1
  1024
  50
  0
  200
END TEST
```
