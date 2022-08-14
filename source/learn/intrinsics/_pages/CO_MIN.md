## co_min

### **Name**

**co_min**(3) - \[COLLECTIVE\] Minimal value on the current set of images

### **Syntax**

```fortran
call co_min(a, result_image, stat, errmsg)
```

### **Description**

co_min determines element-wise the minimal value of **a** on all images of
the current team. If result_image is present, the minimal values are
returned in **a** on the specified image only and the value of **a** on the
other images become undefined. If result_image is not present, the
value is returned on all images. If the execution was successful and
**stat** is present, it is assigned the value zero. If the execution failed,
**stat** gets assigned a nonzero value and, if present, **errmsg** gets assigned
a value describing the occurred error.

### **Arguments**

- **a**
  : shall be an integer, real or character variable, which has the same
  type and type parameters on all images of the team.

- **result_image**
  : (optional) a scalar integer expression; if present, it shall have
  the same the same value on all images and refer to an image of the
  current team.

- **stat**
  : (optional) a scalar integer variable

- **errmsg**
  : (optional) a scalar character variable

### **Examples**

Sample program:

```fortran
program demo_co_min
implicit none
integer :: val
   val = this_image()
   call co_min(val, result_image=1)
   if (this_image() == 1) then
     write(*,*) "Minimal value", val  ! prints 1
   endif
end program demo_co_min
```

### **Standard**

TS 18508 or later

### **See Also**

[**co_max**(3)](CO_MAX),
[**co_sum**(3)](CO_SUM),
[**co_reduce**(3)](CO_REDUCE),
[**co_broadcast**(3)](CO_BROADCAST)

####### fortran-lang intrinsic descriptions