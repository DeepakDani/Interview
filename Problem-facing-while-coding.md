Map reduce program: --
1.it is map and reduce in small letter.
2.hasnext will be with values. 
3,tool & Toolrunner are throwing warning 'The type Tool is deprecated'(Solution: add in code @SuppressWarnings("deprecation")
)
4.java.lang.UnsupportedClassVersionError: MapReduce/DriverCode : Unsupported major.minor version 52.0(solution :This is because of a higher JDK during compile time and lower JDK during runtime. So you just need to update your JDK version, possible to JDK 7)
