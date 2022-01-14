Imshow Extents can now be expressed in Units
--------------------------------------------
The extent parameter of `~axes.Axes.imshow` can now be expressed
with Units. If extent[0] is expressed in units, then so must extent[1].
Similarly, this applies to extent[2] and extent[3] as well. The user is 
responsible to ensure that the units are lined up.

.. plot::
    :include-source: true
    
    import matplotlib.pyplot as plt
    import numpy as np
    from matplotlib.dates import HourLocator, DateFormatter
    from matplotlib.ticker import (AutoMinorLocator)


    fig, ax = plt.subplots()
    dates = np.arange("2020-01-01","2020-01-13", dtype='datetime64[h]')

    arr = [[i+j for i in range(10)] for j in range(10)]

    ax.imshow(arr, origin='lower', extent=[dates[0], dates[10], dates[10], dates[0]])

    ax.xaxis.set_major_formatter(DateFormatter('%d/%m:%H'))
    ax.xaxis.set_major_locator(HourLocator(byhour=[0, 2, 4, 6, 8, 10]))
    ax.xaxis.set_minor_locator(AutoMinorLocator())

    plt.show()