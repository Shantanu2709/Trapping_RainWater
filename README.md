# Trapping_RainWater
Trapping_RainWater Code for linear time complexity...

    static void trapped_water(int height[])
    {
        int n = height.length;
        //Calculate left max boundary
        int leftMax[] = new int[n];
        leftMax[0]=height[0];
        for(int i=1; i<n; i++)
        {
            leftMax[i]=Math.max(height[i],leftMax[i-1]);
        }
        
        //Calculate right max boundary
        int rightMax[] = new int[n];
        rightMax[n-1]=height[n-1];
        for(int i=n-2; i>=0; i--)
        {
            rightMax[i]=Math.max(height[i],rightMax[i+1]);
        }
        
        //Loop
        //Calculate water level = min(leftMax , rightMax)
        //Calculate trapped water volume = (water level - height)
        int trappedWater =0;
        for(int i=0; i<n; i++)
        {
            int waterLevel = Math.min(leftMax[i],rightMax[i]);
            trappedWater+=(waterLevel-height[i]);

        }
        return trappedWater;

    }
