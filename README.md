# Capped Accumulated Return Call Valuation with Lock-In Feature

A Monte Carlo (Gaussian MC and Quasi MC) pricing model is presented for the product named capped-accumulated-return-call (CARC) with lock in feature.  Let  be an increasing series of lock in returns. Let   be the greatest lock in return such that the maximum of the partial accumulated returns is greater or equal than  . If   exists, then the final accumulated return will not be smaller than  . By its definition   is path-dependent. It acts as a path-dependent floor, as opposed to the global floor which is fixed.

Let   be M stocks in a given basket,   be the price process of the jth stock and  , and   be a set of reset dates and   be a payoff settlement date.  The CARC with the multiple underlyings   is a European type derivative security whose matured payoff at the settlement date is given by

	 	(1)

where   is the global floor of the return rate, N is the notional principal, and   is capped-accumulated-return and defined as

	 	(2)

where   is the capped return-rate for each period described as follows:  Define the actual period return-rate as
				 ,	(3)

where

	 .	(4)

Here   are the weights and

	 .	(5)

Then we define

	 ,	(6)

where c is the cap.

The new feature is represented by an increasing series of attributes LOCK_IN_RETURN.
Let  be this series of increasing lock in returns. Define the jth partial accumulated return as follows:  . In particular, the final accumulated return, , is equal to the nth partial accumulated return:  .

Let   be the greatest lock in return such that the maximum of the partial accumulated returns is greater or equal than  , that is  . In our simulation,  is path-dependent (just like  ’s), as opposed to  which is fixed. If there is no such  , that is the set above is empty, we set  . 

We impose that the final accumulated return will not be less than  (see the payoff below).
Let t be the current value date, then the current value of CARC with lock in feature can be written 
	 					
where   is the discounting factor at the value date (note that the inner term is equal to  ).  The above formula is in a world that is forward risk-neutral with respect to a specific currency  .  As a result, the notional principal N is measured in the currency  , and the discounting factor should be calculated by a   zero curve (ref. https://finpricing.com/lib/IrCurveIntroduction.html) given at the value date.  If the underlying asset is measured in another currency  , assuming the option is a Quanto type transaction, the governing price dynamics of the underlying asset in the risk-neutral world of   should be written as

	 	(8)

where   is the short rate of  , q is the dividend yield of the asset,   is the volatility of the asset price,   is the volatility of the exchange rate between   and  ,   is correlation coefficient between the asset price and the exchange rate, and   is the Wiener process.  All these parameters are assumed deterministic.

Quasi-Monte Carlo (GED QMC) simulation method with Sobol sequence associated with Brownian Bridge path generation was used to calculate the option price.  GED used 8,000 simulations and 2,000 stratified samples. Also results obtained using crude Monte Carlo method (GED MC) at 100,000 simulations are reported.



