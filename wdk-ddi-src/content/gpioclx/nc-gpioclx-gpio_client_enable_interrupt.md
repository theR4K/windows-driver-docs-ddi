---
UID: NC:gpioclx.GPIO_CLIENT_ENABLE_INTERRUPT
title: GPIO_CLIENT_ENABLE_INTERRUPT (gpioclx.h)
description: The CLIENT_EnableInterrupt event callback function enables interrupts on a general-purpose I/O (GPIO) pin that is configured as an interrupt input.
old-location: gpio\client_enableinterrupt.htm
tech.root: GPIO
ms.date: 02/15/2018
keywords: ["GPIO_CLIENT_ENABLE_INTERRUPT callback function"]
ms.keywords: CLIENT_EnableInterrupt, CLIENT_EnableInterrupt callback, CLIENT_EnableInterrupt callback function [Parallel Ports], GPIO.client_enableinterrupt, GPIO_CLIENT_ENABLE_INTERRUPT, gpioclx/CLIENT_EnableInterrupt
req.header: gpioclx.h
req.include-header: 
req.target-type: Desktop
req.target-min-winverclnt: Supported starting with Windows 8.
req.target-min-winversvr: 
req.kmdf-ver: 
req.umdf-ver: 
req.ddi-compliance: 
req.unicode-ansi: 
req.idl: 
req.max-support: 
req.namespace: 
req.assembly: 
req.type-library: 
req.lib: 
req.dll: 
req.irql: Called at PASSIVE_LEVEL.
targetos: Windows
req.typenames: 
f1_keywords:
 - GPIO_CLIENT_ENABLE_INTERRUPT
 - gpioclx/GPIO_CLIENT_ENABLE_INTERRUPT
topic_type:
 - APIRef
 - kbSyntax
api_type:
 - UserDefined
api_location:
 - Gpioclx.h
api_name:
 - GPIO_CLIENT_ENABLE_INTERRUPT
---

# GPIO_CLIENT_ENABLE_INTERRUPT callback function


## -description

The <i>CLIENT_EnableInterrupt</i> event callback function enables interrupts on a general-purpose I/O (GPIO) pin that is configured as an interrupt input.

## -parameters

### -param Context [in]


A pointer to the GPIO controller driver's <a href="/windows-hardware/drivers/gpio/gpio-device-contexts">device context</a>.

### -param EnableParameters

### -param InterruptParameters 
[in]
A pointer to a <a href="/windows-hardware/drivers/ddi/gpioclx/ns-gpioclx-_gpio_enable_interrupt_parameters">GPIO_ENABLE_INTERRUPT_PARAMETERS</a> structure that specifies a GPIO pin and describes the interrupt attributes of this pin.

## -returns

The <i>CLIENT_EnableInterrupt</i> function returns STATUS_SUCCESS if the call is successful. Otherwise, it returns an appropriate error code.

## -remarks

This callback function is implemented by the GPIO controller driver. The GPIO framework extension (GpioClx) calls this function to enable interrupts on a GPIO pin that is configured as an interrupt request input.

To register your driver's <i>CLIENT_EnableInterrupt</i> callback function, call the <a href="/windows-hardware/drivers/ddi/gpioclx/nf-gpioclx-gpio_clx_registerclient">GPIO_CLX_RegisterClient</a> method. This method accepts, as an input parameter, a pointer to a <a href="/windows-hardware/drivers/ddi/gpioclx/ns-gpioclx-_gpio_client_registration_packet">GPIO_CLIENT_REGISTRATION_PACKET</a> structure that contains a <i>CLIENT_EnableInterrupt</i> function pointer.

GpioClx always calls the <i>CLIENT_EnableInterrupt</i> and <a href="/windows-hardware/drivers/ddi/gpioclx/nc-gpioclx-gpio_client_disable_interrupt">CLIENT_DisableInterrupt</a> callback functions at IRQL = PASSIVE_LEVEL. However, if the GPIO registers are memory-mapped, GpioClx calls the other interrupt-related callback functions from its ISR at DIRQL. In this case, the <i>CLIENT_EnableInterrupt</i> and <i>CLIENT_DisableInterrupt</i> functions should use the GPIO interrupt lock to synchronize their interrupt-related operations to the ISR. For more information, see <a href="/windows-hardware/drivers/gpio/interrupt-synchronization-for-gpio-controller-drivers">Interrupt Synchronization for GPIO Controller Drivers</a>.


#### Examples

To define a <i>CLIENT_EnableInterrupt</i> callback function, you must first provide a function declaration that identifies the type of callback function you're defining. Windows provides a set of callback function types for drivers. Declaring a function using the callback function types helps <a href="/windows-hardware/drivers/devtest/code-analysis-for-drivers">Code Analysis for Drivers</a>, <a href="/windows-hardware/drivers/devtest/static-driver-verifier">Static Driver Verifier</a> (SDV), and other verification tools find errors, and it's a requirement for writing drivers for the Windows operating system.

For example, to define a <i>CLIENT_EnableInterrupt</i> callback function that is named <code>MyEvtGpioEnableInterrupt</code>, use the GPIO_CLIENT_ENABLE_INTERRUPT function type, as shown in this code example:


```
GPIO_CLIENT_ENABLE_INTERRUPT MyEvtGpioEnableInterrupt;
```

Then, implement your callback function as follows:


```
_Use_decl_annotations_
NTSTATUS
  MyEvtGpioEnableInterrupt(
    PVOID Context,
    PGPIO_ENABLE_INTERRUPT_PARAMETERS InterruptParameters
    )
{ ... }
```

The GPIO_CLIENT_ENABLE_INTERRUPT function type is defined in the Gpioclx.h header file. To more accurately identify errors when you run the code analysis tools, be sure to add the _Use_decl_annotations_ annotation to your function definition. The _Use_decl_annotations_ annotation ensures that the annotations that are applied to the GPIO_CLIENT_ENABLE_INTERRUPT function type in the header file are used. For more information about the requirements for function declarations, see <a href="/windows-hardware/drivers/devtest/declaring-functions-by-using-function-role-types-for-kmdf-drivers">Declaring Functions by Using Function Role Types for KMDF Drivers</a>. For more information about _Use_decl_annotations_, see <a href="/visualstudio/code-quality/annotating-function-behavior">Annotating Function Behavior</a>.

<div class="code"></div>

## -see-also

<a href="/windows-hardware/drivers/ddi/gpioclx/nc-gpioclx-gpio_client_disable_interrupt">CLIENT_DisableInterrupt</a>



<a href="/windows-hardware/drivers/ddi/gpioclx/ns-gpioclx-_gpio_client_registration_packet">GPIO_CLIENT_REGISTRATION_PACKET</a>



<a href="/windows-hardware/drivers/ddi/gpioclx/nf-gpioclx-gpio_clx_registerclient">GPIO_CLX_RegisterClient</a>



<a href="/windows-hardware/drivers/ddi/gpioclx/ns-gpioclx-_gpio_enable_interrupt_parameters">GPIO_ENABLE_INTERRUPT_PARAMETERS</a>

