const _validateAssessPATEligibilityV2Request = body => {  
  // Mock the validation in PATRuleService/AssessPATEligibilityV2Request  
  let errorList = []  
  
  errorList = errorList.concat(_validateApplication(body))  
  errorList = errorList.concat(_validateCompany(body))  
  errorList = errorList.concat(_validateCurrentIssuedPass(body))  
  
  if (errorList.length > 0) throw new Error(errorList)  
}

src/api/pat/pat-v2.js