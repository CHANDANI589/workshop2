# Super Assets Integration

# Super Assets Integration

This module provides utilities for working with Super Assets on Superposition.

## Overview

Super Assets are yield-bearing wrapped tokens that pay rewards for both holding AND using them.
When you bridge assets to Superposition, they automatically become Super Assets.

## Key Features

- **Passive Yield**: Earn yield just by holding Super Assets
- **Active Yield**: Earn additional rewards when using them in transactions
- **Utility Mining**: Every transaction earns potential token rewards

## Supported Super Assets

- **sUSDC**
- **sETH**

## Usage

### Wrapping/Unwrapping

```typescript
import { useSuperAsset } from './hooks/useSuperAsset';

function WrapComponent() {
  const { wrap, unwrap, status } = useSuperAsset('sUSDC');

  const handleWrap = async () => {
    await wrap(parseUnits('100', 6)); // Wrap 100 USDC to sUSDC
  };

  const handleUnwrap = async () => {
    await unwrap(parseUnits('100', 6)); // Unwrap 100 sUSDC to USDC
  };
}
```


### Tracking Yield

```typescript
import { useSuperAssetYield } from './hooks/useSuperAssetYield';

function YieldDisplay() {
  const { pendingYield, currentApy, claimYield } = useSuperAssetYield('sUSDC');

  return (
    <div>
      <p>Current APY: {currentApy}%</p>
      <p>Pending Yield: {formatUnits(pendingYield, 6)} sUSDC</p>
      <button onClick={claimYield}>Claim Yield</button>
    </div>
  );
}
```



### Balance Display

```typescript
import { SuperAssetBalanceDisplay } from './components/SuperAssetBalanceDisplay';

function Dashboard() {
  return <SuperAssetBalanceDisplay />;
}
```


## Resources

- [Super Assets Documentation](https://docs.superposition.so/superposition-mainnet/super-layer/super-assets)
- [Superposition Bridge](https://bridge.superposition.so)