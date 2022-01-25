# kuacc-info

Gives cluster usage summary (CPUs, MEMs, Nodes).<br>
There are two parts of command output. First part  lists users, their running and pending jobs number, node usage of users, cpus usage of users and memory usage of users on KUACC(IT) nodes(kcc) – cosmos(csms) nodes – ilac nodes(ilc) – ai nodes.<br>
Second part of command output is very useful. It gives detailed version of sinfo command. Following output is second part of command output. Name of node, its partition, cpu usage, mem usage and status of node.<br>

```
------------------------------------------------------------------------------------------------------------
                NAME          TYPE            CPU_USAGE     MEM_USAGE     STATUS
------------------------------------------------------------------------------------------------------------
                ag01         COSBI             7 ( 87%)    55.25 ( 45%)   BUSY
                ai01            AI            38 ( 95%)   186.88 ( 38%)   BUSY
                ai02            AI             0 (  0%)     0.00 (  0%)   FREE
                ai03            AI            36 ( 90%)   319.00 ( 64%)   BUSY
                ai04            AI            20 ( 50%)   211.00 ( 42%)   BUSY
                ai05            AI            19 ( 47%)   176.00 ( 35%)   BUSY
                ai06            AI             5 ( 12%)    60.00 ( 12%)   BUSY
                ai07            AI            38 ( 95%)   164.00 ( 33%)   BUSY
                ai08            AI            26 ( 65%)   148.00 ( 30%)   BUSY
                ai09            AI            29 ( 72%)   134.00 ( 27%)   BUSY
                ai10            AI            34 ( 85%)   256.00 ( 52%)   BUSY
                ai11            AI            35 ( 87%)   484.00 ( 98%)   FULL(MEM)
                ai12            AI            37 ( 92%)   406.30 ( 82%)   BUSY
                ai13            AI            26 ( 65%)   468.14 ( 95%)   FULL(MEM)
                ai14            AI            24 ( 60%)   378.00 ( 76%)   BUSY
                be01          ILAC            12 (100%)    48.00 ( 39%)   FULL(CPU)
                be02          ILAC            12 (100%)    48.00 ( 39%)   FULL(CPU)
                be03          ILAC            12 (100%)    48.00 ( 39%)   FULL(CPU)
                be04          ILAC            11 ( 91%)    44.00 ( 35%)   BUSY
                be05          ILAC            12 (100%)    48.00 ( 39%)   FULL(CPU)
                be06          ILAC            11 ( 91%)    44.00 ( 35%)   BUSY
                be07          ILAC             8 ( 66%)    32.00 ( 26%)   BUSY
                be08          ILAC            12 (100%)   123.05 (100%)   FULL(CPU)
                be09          ILAC            12 (100%)    56.00 ( 45%)   FULL(CPU)
                be10          ILAC            12 (100%)    56.00 ( 45%)   FULL(CPU)
                be11          ILAC             0 (  0%)     0.00 (  0%)   FREE
                be12          ILAC             0 (  0%)     0.00 (  0%)   FREE
          buyukliman         HAMSI            18 ( 25%)   108.00 ( 44%)   BUSY
                da01       BIYOFIZ            10 ( 50%)    40.00 ( 16%)   BUSY
                da02       BIYOFIZ            10 ( 50%)    40.00 ( 16%)   BUSY
                da03       BIYOFIZ            10 ( 50%)    40.00 ( 16%)   BUSY
                da04       BIYOFIZ             3 ( 15%)   140.00 ( 57%)   BUSY
                dy02            AI            36 (100%)   144.00 ( 29%)   FULL(CPU)
                dy03            AI             2 (  8%)    78.12 ( 17%)   BUSY
                it01         KUACC            26 ( 65%)   104.00 ( 21%)   BUSY
                it02         KUACC            10 ( 25%)    40.00 (  8%)   BUSY
                it03         KUACC            35 ( 87%)   140.00 ( 28%)   BUSY
                it04         KUACC            38 ( 95%)   192.00 ( 39%)   BUSY
                ke01        COSMOS            36 (100%)   217.66 ( 44%)   FULL(CPU)
                ke02        COSMOS            35 ( 97%)   242.48 ( 49%)   FULL(CPU)
                ke03        COSMOS            36 (100%)   225.66 ( 45%)   FULL(CPU)
                ke04        COSMOS            36 (100%)   231.66 ( 47%)   FULL(CPU)
                ke05        COSMOS            36 (100%)   198.83 ( 40%)   FULL(CPU)
                ke06        COSMOS            36 (100%)   190.83 ( 38%)   FULL(CPU)
                ke07        COSMOS            36 (100%)   198.83 ( 40%)   FULL(CPU)
                ke08        COSMOS            35 ( 97%)   160.00 ( 32%)   FULL(CPU)
                rk01         KUTEM            40 ( 55%)   240.00 ( 48%)   BUSY
                sm01           IUI             4 ( 20%)    24.00 ( 38%)   BUSY
```

⚠️⚠️⚠️ Command output is useful while submitting jobs. User can find a free resource and submit job on these nodes by nodelist or constraint flags.
