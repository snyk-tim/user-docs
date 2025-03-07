# AI Engine

Snyk Code is powered by a semantic, AI-based analysis engine. This AI engine can analyze the following in your code:

### **Hardcoded secrets**

Snyk Code includes secret detection capabilities that scan and highlight secrets like keys, credentials, PII, and sensitive information in your source code. Unlike tools that use entropy checks or regular expressions, Snyk Code uses machine learning and is able to learn from experience, improving the odds of accurately detecting secrets while minimizing false positives.

![](../../../.gitbook/assets/image5.png)

### **Coding issues**

Problems such as dead code, branches that are predefined, and branches having the same code on each side.

### **Type inference**

Determining the initial type and its changes; this is of special interest for dynamically typed languages.

### **Value ranges**

Infers possible values for variables used to call functions to track off-by-one errors in arrays, division-by-zero, and null dereferences.

### **Data flow**

Follows the flow of data within the application, from the source to the sink. Combined with AI-based learning of external insecure data source, data sinks, and sanitation functions, this enables a strong taint analysis.

### **API usage**

Using open source or the documentation of frameworks to learn how functions need to be used, can identify API misuse such as using the wrong parameter type or calling with the wrong value range. This mechanism can also identify use of insecure functions.

### **Control Flow**

Identifies null dereference or race conditions by modeling each possible control flow in the application.

### **Point-to Analysis**

Identifies multiple possible issues including from buffer overruns, null dereferences, and type mismatches, by modeling the usage of memory in variables and references.
