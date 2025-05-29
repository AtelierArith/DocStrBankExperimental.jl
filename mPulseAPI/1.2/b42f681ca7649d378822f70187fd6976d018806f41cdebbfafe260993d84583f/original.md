Internal convenience function.  Fetches an object from the repository and caches it for an hour in the appropriate cache object

  * Returns a single object if `searchKey`s are passed in an `filterRequired` is set to `true` (default)
  * Returns an array of objects if `searchKey`s are not passed in and `filterRequired` is set to `false`
  * Throws an exception if `searchKey`s are not passed in and `filterRequired` is set to `true`
