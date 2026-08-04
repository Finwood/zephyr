.. _adc_api:

Analog-to-Digital Converter (ADC)
#################################

Overview
********

The ADC API converts raw sample values to millivolts using a per-channel
reference configuration.  For channels that use :c:enumerator:`ADC_REF_INTERNAL`,
the millivolt scale comes from the driver: most drivers expose a static
:c:member:`adc_driver_api.ref_internal` value, while drivers that support
runtime updates may implement optional :c:member:`adc_driver_api.vref_get` and
:c:member:`adc_driver_api.vref_set` callbacks.  Use :c:func:`adc_ref_internal`
to read the current internal reference in millivolts and
:c:func:`adc_ref_internal_set` to update it when the driver supports that
operation.

The devicetree property ``zephyr,vref-mv`` remains the way to specify a fixed
millivolt reference for channels that do **not** use
:c:enumerator:`ADC_REF_INTERNAL`.  That property is not routed through
:c:member:`adc_driver_api.vref_get` in this release.

API Reference
*************

.. doxygengroup:: adc_interface
