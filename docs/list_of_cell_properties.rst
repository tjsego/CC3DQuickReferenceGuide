List of cell properties
======================================================================================

.. csv-table::
    :header: "Name", "Command", "Fixed?", "Comments"
    :widths: 30, 40, 13, 68

    Cell identity, ``cell.id``, Yes, Unique cell identification number
    Cell type, ``cell.type``, No, Specifies the type of the cell
    Cell volume, ``cell.volume``, Yes, Instantaneous cell volume
    , ``cell.targetVolume``, No, Target value of volume constraint
    , ``cell.lambdaVolume``, No, Lambda of the volume constraint
    Cell surface [#f1]_, ``cell.surface``, Yes, Instantaneous cell surface
    , ``cell.targetSurface``, No, Target value of surface constraint
    , ``cell.lambdaSurface``, No, Lambda of the surface constraint
    Center of mass [#f2]_, ``cell.xCOM``, Yes, Cartesian coordinate *x* of center of mass
    , ``cell.yCOM``, Yes, Cartesian coordinate *y* of center of mass
    , ``cell.zCOM``, Yes, Cartesian coordinate *z* of center of mass
    Eccentricity [#f3]_, ``cell.ecc``, Yes, Eccentricity of cell
    Inertia tensor [#f3]_, ``cell.iXX``, Yes, Moment of inertia *x*-axis about the *x*-axis
    , ``cell.iYY``, Yes, Moment of inertia *y*-axis about the *y*-axis
    , ``cell.iZZ``, Yes, Moment of inertia *z*-axis about the *z*-axis
    , ``cell.iXY``, Yes, Moment of inertia *x*-axis about the *y*-axis
    , ``cell.iXZ``, Yes, Moment of inertia *x*-axis about the *z*-axis
    , ``cell.iYZ``, Yes, Moment of inertia *y*-axis about the *z*-axis
    Minor axis vector [#f3]_, ``cell.lX``, Yes, Component *x* of the vector along semiminor axis
    , ``cell.lY``, Yes, Component *y* of the vector along semiminor axis
    , ``cell.lZ``, Yes, Component *z* of the vector along semiminor axis
    Directional forces [#f4]_, ``cell.lambdaVecX``, No, Force component acting on the *x*-direction
    , ``cell.lambdaVecY``, No, Force component acting on the *y*-direction
    , ``cell.lambdaVecZ``, No, Force component acting on the *z*-direction

.. footnotes::csv-table
.. [#f1] Only available when ``Surface`` , ``SurfaceTracker``, ``SurfaceFlex`` or ``SurfaceLocalFlex`` plugins are called.
.. [#f2] Only available when ``CenterOfMass`` plugin is called.
.. [#f3] Only available when ``MomentOfInertia`` plugin is called.
.. [#f4]  Only available when ``ExternalPotential`` plugin is called.
