using LibGit2Sharp;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace libgit2sharp_test
{
    class Program
    {
        static void Main(string[] args)
        {
            using (var newRepository = Repository.Clone(@"https://github.com/shinetech-china-tianjin/VpnAddressTracer.git", "test"))
            {
            }

            using (var repository = new Repository("test"))
            {
                var master = repository.Branches.First(b => b.Name.Contains("master"));
                var sign = new Signature("Lu Rongkai", "", DateTimeOffset.Now);
                foreach (var changed in repository.Diff.Compare())
                {
                    repository.Index.Stage(changed.Path);
                }
                repository.Commit("test", sign);

                var credentials = new Credentials() { Username = "", Password = "" };
                repository.Network.Push(master.Remote, repository.Head.CanonicalName, credentials);
            }

            Console.ReadLine();
        }
    }
}
