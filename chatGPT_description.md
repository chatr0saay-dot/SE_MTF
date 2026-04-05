# Slanted-edge MTF50 measurement (core methods text)

Spatial frequency performance was quantified using slanted-edge analysis of high-contrast edge images acquired under identical imaging settings across all conditions. The edge target was oriented obliquely relative to the detector sampling grid to enable sub-pixel phase diversity. To reduce bias from camera-internal processing, analysis used raw images or linear 16-bit renders from raw data whenever available.

For each image, a rectangular region of interest (ROI) containing the edge transition and local background was selected after excluding saturated pixels. The edge location and orientation were estimated within the ROI, and each pixel center was projected onto the axis normal to the fitted edge. Pixel intensities were then re-indexed by signed edge-normal distance to construct an oversampled edge spread function (ESF) at sub-pixel spacing. Here, \(d\) denotes signed distance along the edge-normal axis and \(f\) denotes spatial frequency.

## Core equations

The edge spread function, line spread function, and modulation transfer function were defined as

$$
\begin{aligned}
E(d) &= \text{edge spread function}, \\
L(d) &= \frac{\mathrm{d}E(d)}{\mathrm{d}d}, \\
\operatorname{MTF}(f) &= \frac{\left| \mathcal{F}\{L(d)\}(f) \right|}{\left| \mathcal{F}\{L(d)\}(0) \right|}.
\end{aligned}
$$

To mitigate truncation artifacts and suppress high-frequency noise, the LSF was multiplied by an apodization window before Fourier transformation. MTF50 was defined as the spatial frequency \(f_{50}\) satisfying

$$
\operatorname{MTF}(f_{50}) = 0.5,
$$

with \(f_{50}\) estimated by interpolation between adjacent sampled frequency bins.

Frequencies were first reported in cycles per pixel. Where required, values were converted to image-plane and object-plane line pairs per millimeter (lp/mm) as

$$
\begin{aligned}
f_{\mathrm{image}}^{(\mathrm{lp/mm})} &= \frac{f_{\mathrm{pixel}}^{(\mathrm{cy/pixel})}}{p}, \\
f_{\mathrm{object}}^{(\mathrm{lp/mm})} &= \frac{M\,f_{\mathrm{pixel}}^{(\mathrm{cy/pixel})}}{p},
\end{aligned}
$$

where \(p\) is the detector pixel pitch in mm/pixel and \(M\) is the system magnification.
Unless otherwise stated, all comparisons used matched edge targets, acquisition settings, preprocessing conditions, and analysis parameters.

## Notes for manuscript adaptation

- In sampled digital systems, this edge-derived metric is often termed spatial frequency response (SFR); here, the conventional term MTF50 is used for consistency with common reporting practice.
- For biomedical manuscripts, explicitly report edge angle, ROI size, window type, interpolation scheme, and whether demosaicing/sharpening was disabled.

## References

1. ISO 12233:2017. *Photography — Electronic still picture imaging — Resolution and spatial frequency responses.* International Organization for Standardization.
2. van den Bergh F. et al. *Robust edge spread function construction methods to counter the effects of correlated noise.* (edge-based MTF/SFR methodology).
